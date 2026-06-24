# Highlevel (part 2)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

```

# -*- coding: utf-8 -*-
"""High level Visa library wrapper.

This file is part of PyVISA.

:copyright: 2014-2024 by PyVISA Authors, see AUTHORS for more details.
:license: MIT, see LICENSE for more details.

"""

import atexit
import contextlib
import copy
import os
import pkgutil
import warnings
from collections import defaultdict
from importlib import import_module
from itertools import chain
from types import ModuleType
from typing import (
    TYPE_CHECKING,
    Any,
    Callable,
    ContextManager,
    Dict,
    Iterable,
    Iterator,
    List,
    NamedTuple,
    Optional,
    Set,
    SupportsBytes,
    Tuple,
    Type,
    TypeVar,
    Union,
    cast,
)
from weakref import WeakMethod, WeakSet, WeakValueDictionary

from typing_extensions import ClassVar, DefaultDict, Literal

from . import attributes, constants, errors, logger, rname
from .constants import StatusCode
from .typing import (
    VISAEventContext,
    VISAHandler,
    VISAJobID,
    VISAMemoryAddress,
    VISARMSession,
    VISASession,
)
from .util import DebugInfo, LibraryPath

if TYPE_CHECKING:
    from .resources import Resource  # pragma: no cover

#: Resource extended information
#:
#: Named tuple with information about a resource. Returned by some :class:`ResourceManager` methods.
#:
#: :interface_type: Interface type of the given resource string. :class:`pyvisa.constants.InterfaceType`
#: :interface_board_number: Board number of the interface of the given resource string. We allow None
#:                          since serial resources may not sometimes be easily described
#:                          by a single number in particular on Linux system.
#: :resource_class: Specifies the resource class (for example, "INSTR") of the given resource string.
#: :resource_name: This is the expanded version of the given resource string.
#:                 The format should be similar to the VISA-defined canonical resource name.
#: :alias: Specifies the user-defined alias for the given resource string.
ResourceInfo = NamedTuple(
    "ResourceInfo",
    (
        ("interface_type", constants.InterfaceType),
        ("interface_board_number", Optional[int]),
        ("resource_class", Optional[str]),
        ("resource_name", Optional[str]),
        ("alias", Optional[str]),
    ),
)

# Used to properly type the __new__ method
T = TypeVar("T", bound="VisaLibraryBase")

[docs]
class VisaLibraryBase(object):
    """Base for VISA library classes.

    A class derived from `VisaLibraryBase` library provides the low-level communication
    to the underlying devices providing Pythonic wrappers to VISA functions. But not all
    derived class must/will implement all methods. Even if methods are expected to return
    the status code they are expected to raise the appropriate exception when an error
    occurred since this is more Pythonic.

    The default VisaLibrary class is :class:`pyvisa.ctwrapper.highlevel.IVIVisaLibrary`,
    which implements a ctypes wrapper around the IVI-VISA library.
    Certainly, IVI-VISA can be NI-VISA, Keysight VISA, R&S VISA, tekVISA etc.

    In general, you should not instantiate it directly. The object exposed to the user
    is the :class:`pyvisa.highlevel.ResourceManager`. If needed, you can access the
    VISA library from it::

        >>> import pyvisa
        >>> rm = pyvisa.ResourceManager("/path/to/my/libvisa.so.7")
        >>> lib = rm.visalib

    """

    #: Default ResourceManager instance for this library.
    resource_manager: Optional["ResourceManager"]

    #: Path to the VISA library used by this instance
    library_path: LibraryPath

    #: Maps library path to VisaLibrary object
    _registry: ClassVar[
        Dict[Tuple[Type["VisaLibraryBase"], LibraryPath], "VisaLibraryBase"]
    ] = WeakValueDictionary()  # type: ignore

    #: Last return value of the library.
    _last_status: StatusCode = StatusCode(0)

    #: Maps session handle to last status.
    _last_status_in_session: Dict[
        Union[VISASession, VISARMSession, VISAEventContext], StatusCode
    ]

    #: Maps session handle to warnings to ignore.
    _ignore_warning_in_session: Dict[int, set]

    #: Extra information used for logging errors
    _logging_extra: Dict[str, str]

    #: Contains all installed event handlers.
    #: Its elements are tuples with four elements: The handler itself (a Python
    #: callable), the user handle (in any format making sense to the lower level
    #: implementation, ie as a ctypes object for the ctypes backend) and the
    #: handler again, this time in a format meaningful to the backend (ie as a
    #: ctypes object created with CFUNCTYPE for the ctypes backend) and
    #: the event type.
    handlers: DefaultDict[VISASession, List[Tuple[VISAHandler, Any, Any, Any]]]

    #: Set error codes on which to issue a warning.
    issue_warning_on: Set[StatusCode]

    def __new__(
        cls: Type[T], library_path: Union[str, LibraryPath] = ""
    ) -> "VisaLibraryBase":
        """Create a new VISA library from the specified path.

        If a library was already created using the same path and class this
        library object is returned instead.

        Parameters
        ----------
        library_path : str | LibraryPath
            Path to the VISA library to use in the backend.

        Raises
        ------
        OSError
            Raised if the VISA library object could not be created.

        """
        if library_path == "":
            errs = []
            for path in cls.get_library_paths():
                try:
                    return cls(path)
                except OSError as e:
                    logger.debug("Could not open VISA library %s: %s", path, str(e))
                    errs.append(str(e))
                except Exception as e:
                    errs.append(str(e))
            else:
                raise OSError("Could not open VISA library:\n" + "\n".join(errs))

        if not isinstance(library_path, LibraryPath):
            lib_path = LibraryPath(library_path, "user specified")
        else:
            lib_path = library_path

        if (cls, lib_path) in cls._registry:
            return cls._registry[(cls, lib_path)]

        obj = super(VisaLibraryBase, cls).__new__(cls)

        obj.library_path = lib_path

        obj._logging_extra = {"library_path": obj.library_path}

        obj._init()

        # Create instance specific registries.
        #: Error codes on which to issue a warning.
        obj.issue_warning_on = set(errors.default_warnings)
        obj._last_status_in_session = {}
        obj._ignore_warning_in_session = defaultdict(set)
        obj.handlers = defaultdict(list)
        obj.resource_manager = None

        logger.debug("Created library wrapper for %s", lib_path)

        cls._registry[(cls, lib_path)] = obj

        return obj

[docs]
    @staticmethod
    def get_library_paths() -> Iterable[LibraryPath]:
        """Override to list the possible library_paths if no path is specified."""
        return ()

[docs]
    @staticmethod
    def get_debug_info() -> DebugInfo:
        """Override to return an iterable of lines with the backend debug details."""
        return ["Does not provide debug info"]

    def _init(self) -> None:
        """Override this method to customize VisaLibrary initialization."""
        pass

    def __str__(self) -> str:
        """str representation of the library."""
        return "Visa Library at %s" % self.library_path

    def __repr__(self) -> str:
        """str representation of the library including the type of the library."""
        return "<%s(%r)>" % (type(self).__name__, self.library_path)

[docs]
    def handle_return_value(
        self,
        session: Optional[Union[VISAEventContext, VISARMSession, VISASession]],
        status_code: int,
    ) -> StatusCode:
        """Helper function handling the return code of a low-level operation.

        Used when implementing concrete subclasses of VISALibraryBase.

        """
        rv: StatusCode
        try:
            rv = StatusCode(status_code)
        except ValueError:
            rv = cast(StatusCode, status_code)

        self._last_status = rv

        if session is not None:
            self._last_status_in_session[session] = rv

        if rv < 0:
            raise errors.VisaIOError(rv)

        if rv in self.issue_warning_on:
            if session and rv not in self._ignore_warning_in_session[session]:
                warnings.warn(errors.VisaIOWarning(rv), stacklevel=2)

        # Return the original value for further processing.
        return rv

    @property
    def last_status(self) -> StatusCode:
        """Last return value of the library."""
        return self._last_status

[docs]
    def get_last_status_in_session(
        self, session: Union[VISASession, VISARMSession]
    ) -> StatusCode:
        """Last status in session.

        Helper function to be called by resources properties.

        """
        try:
            return self._last_status_in_session[session]
        except KeyError:
            raise errors.Error(
                "The session %r does not seem to be valid as it does not have any last status"
                % session
            )

[docs]
    @contextlib.contextmanager
    def ignore_warning(
        self,
        session: Union[VISASession, VISARMSession],
        *warnings_constants: StatusCode,
    ) -> Iterator:
        """Ignore warnings for a session for the duration of the context.

        Parameters
        ----------
        session : Union[VISASession, VISARMSession]
            Unique logical identifier to a session.
        warnings_constants : StatusCode
            Constants identifying the warnings to ignore.

        """
        self._ignore_warning_in_session[session].update(warnings_constants)
        yield
        self._ignore_warning_in_session[session].difference_update(warnings_constants)

[docs]
    def install_visa_handler(
        self,
        session: VISASession,
        event_type: constants.EventType,
        handler: VISAHandler,
        user_handle: Any = None,
    ) -> Any:
        """Installs handlers for event callbacks.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType,
            Logical event identifier.
        handler : VISAHandler
            Handler to be installed by a client application.
        user_handle :
            A value specified by an application that can be used for identifying
            handlers uniquely for an event type.

        Returns
        -------
        converted_user_handle:
            Converted user handle to match the underlying library. This version
            of the handle should be used in further call to the library.

        """
        try:
            new_handler = self.install_handler(
                session, event_type, handler, user_handle
            )
        except TypeError as e:
            raise errors.VisaTypeError(str(e)) from e

        self.handlers[session].append((*new_handler[:-1], event_type))
        return new_handler[1]

[docs]
    def uninstall_visa_handler(
        self,
        session: VISASession,
        event_type: constants.EventType,
        handler: VISAHandler,
        user_handle: Any = None,
    ) -> None:
        """Uninstalls handlers for events.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Logical event identifier.
        handler : VISAHandler
            Handler to be uninstalled by a client application.
        user_handle :
            The user handle returned by install_visa_handler.

        """
        for ndx, element in enumerate(self.handlers[session]):
            # use == rather than is to allow bound methods as handlers
            if (
                element[0] == handler
                and element[1] is user_handle
                and element[3] == event_type
            ):
                del self.handlers[session][ndx]
                break
        else:
            raise errors.UnknownHandler(event_type, handler, user_handle)
        self.uninstall_handler(session, event_type, element[2], user_handle)

    def __uninstall_all_handlers_helper(self, session: VISASession) -> None:
        """Uninstall all VISA handlers for a given session."""
        for element in self.handlers[session]:
            self.uninstall_handler(session, element[3], element[2], element[1])
        del self.handlers[session]

[docs]
    def uninstall_all_visa_handlers(self, session: Optional[VISASession]) -> None:
        """Uninstalls all previously installed handlers for a particular session.

        Parameters
        ----------
        session : VISASession | None
            Unique logical identifier to a session. If None, operates on all sessions.

        """

        if session is not None:
            self.__uninstall_all_handlers_helper(session)
        else:
            for session in list(self.handlers):
                self.__uninstall_all_handlers_helper(session)

[docs]
    def read_memory(
        self,
        session: VISASession,
        space: constants.AddressSpace,
        offset: int,
        width: Union[Literal[8, 16, 32, 64], constants.DataWidth],
        extended: bool = False,
    ) -> Tuple[int, StatusCode]:
        """Read a value from the specified memory space and offset.

        Corresponds to viIn* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Specifies the address space from which to read.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        width : Union[Literal[8, 16, 32, 64], constants.DataWidth]
            Number of bits to read (8, 16, 32 or 64).
        extended : bool, optional
            Use 64 bits offset independent of the platform.

        Returns
        -------
        data : int
            Data read from memory
        status_code : StatusCode
            Return value of the library call.

        Raises
        ------
        ValueError
            Raised if an invalid width is specified.

        """
        w = width * 8 if isinstance(width, constants.DataWidth) else width
        if w not in (8, 16, 32, 64):
            raise ValueError(
                "%s is not a valid size. Valid values are 8, 16, 32 or 64 "
                "or one member of constants.DataWidth" % width
            )
        return getattr(self, f"in_{w}")(session, space, offset, extended)

[docs]
    def write_memory(
        self,
        session: VISASession,
        space: constants.AddressSpace,
        offset: int,
        data: int,
        width: Union[Literal[8, 16, 32, 64], constants.DataWidth],
        extended: bool = False,
    ) -> StatusCode:
        """Write a value to the specified memory space and offset.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Specifies the address space.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        data : int
            Data to write to bus.
        width : Union[Literal[8, 16, 32, 64], constants.DataWidth]
            Number of bits to read.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        StatusCode
            Return value of the library call.

        Raises
        ------
        ValueError
            Raised if an invalid width is specified.

        """
        w = width * 8 if isinstance(width, constants.DataWidth) else width
        if w not in (8, 16, 32, 64):
            raise ValueError(
                "%s is not a valid size. Valid values are 8, 16, 32 or 64 "
                "or one member of constants.DataWidth" % width
            )
        return getattr(self, f"out_{w}")(session, space, offset, data, extended)

[docs]
    def move_in(
        self,
        session: VISASession,
        space: constants.AddressSpace,
        offset: int,
        length: int,
        width: Union[Literal[8, 16, 32, 64], constants.DataWidth],
        extended: bool = False,
    ) -> Tuple[List[int], StatusCode]:
        """Move a block of data to local memory from the given address space and offset.

        Corresponds to viMoveIn* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space from which to move the data.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        length : int
             Number of elements to transfer, where the data width of
             the elements to transfer is identical to the source data width.
        width : Union[Literal[8, 16, 32, 64], constants.DataWidth]
            Number of bits to read per element.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        data : List[int]
            Data read from the bus
        status_code : StatusCode
            Return value of the library call.

        Raises
        ------
        ValueError
            Raised if an invalid width is specified.

        """
        w = width * 8 if isinstance(width, constants.DataWidth) else width
        if w not in (8, 16, 32, 64):
            raise ValueError(
                "%s is not a valid size. Valid values are 8, 16, 32 or 64 "
                "or one member of constants.DataWidth" % width
            )
        return getattr(self, f"move_in_{w}")(session, space, offset, length, extended)

[docs]
    def move_out(
        self,
        session: VISASession,
        space: constants.AddressSpace,
        offset: int,
        length: int,
        data: Iterable[int],
        width: Union[Literal[8, 16, 32, 64], constants.DataWidth],
        extended: bool = False,
    ) -> StatusCode:
        """Move a block of data from local memory to the given address space and offset.

        Corresponds to viMoveOut* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space into which move the data.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        length : int
            Number of elements to transfer, where the data width of
            the elements to transfer is identical to the source data width.
        data : Iterable[int]
            Data to write to bus.
        width : Union[Literal[8, 16, 32, 64], constants.DataWidth]
            Number of bits to per element.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        StatusCode
            Return value of the library call.

        Raises
        ------
        ValueError
            Raised if an invalid width is specified.

        """
        w = width * 8 if isinstance(width, constants.DataWidth) else width
        if w not in (8, 16, 32, 64):
            raise ValueError(
                "%s is not a valid size. Valid values are 8, 16, 32 or 64 "
                "or one member of constants.DataWidth" % width
            )
        return getattr(self, f"move_out_{w}")(
            session, space, offset, length, data, extended
        )

[docs]
    def peek(
        self,
        session: VISASession,
        address: VISAMemoryAddress,
        width: Union[Literal[8, 16, 32, 64], constants.DataWidth],
    ) -> Tuple[int, StatusCode]:
        """Read an 8, 16, 32, or 64-bit value from the specified address.

        Corresponds to viPeek* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.
        width : Union[Literal[8, 16, 32, 64], constants.DataWidth]
            Number of bits to read.

        Returns
        -------
        data : int
            Data read from bus
        status_code : StatusCode
            Return value of the library call.

        Raises
        ------
        ValueError
            Raised if an invalid width is specified.

        """
        w = width * 8 if isinstance(width, constants.DataWidth) else width
        if w not in (8, 16, 32, 64):
            raise ValueError(
                "%s is not a valid size. Valid values are 8, 16, 32 or 64 "
                "or one member of constants.DataWidth" % width
            )
        return getattr(self, f"peek_{w}")(session, address)

[docs]
    def poke(
        self,
        session: VISASession,
        address: VISAMemoryAddress,
        width: Union[Literal[8, 16, 32, 64], constants.DataWidth],
        data: int,
    ) -> StatusCode:
        """Writes an 8, 16, 32, or 64-bit value from the specified address.

        Corresponds to viPoke* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.
        width : Union[Literal[8, 16, 32, 64], constants.DataWidth]
            Number of bits to read.
        data : int
            Data to write to the bus

        Returns
        -------
        status_code : StatusCode
            Return value of the library call.

        Raises
        ------
        ValueError
            Raised if an invalid width is specified.

        """
        w = width * 8 if isinstance(width, constants.DataWidth) else width
        if w not in (8, 16, 32, 64):
            raise ValueError(
                "%s is not a valid size. Valid values are 8, 16, 32 or 64 "
                "or one member of constants.DataWidth" % width
            )
        return getattr(self, f"poke_{w}")(session, address, data)

    # Methods that VISA Library implementations must implement

[docs]
    def assert_interrupt_signal(
        self,
        session: VISASession,
        mode: constants.AssertSignalInterrupt,
        status_id: int,
    ) -> StatusCode:
        """Asserts the specified interrupt or signal.

        Corresponds to viAssertIntrSignal function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        mode : constants.AssertSignalInterrupt
            How to assert the interrupt.
        status_id : int
            Status value to be presented during an interrupt acknowledge cycle.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
    def assert_trigger(
        self, session: VISASession, protocol: constants.TriggerProtocol
    ) -> StatusCode:
        """Assert software or hardware trigger.

        Corresponds to viAssertTrigger function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        protocol : constants.TriggerProtocol
            Trigger protocol to use during assertion.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
    def assert_utility_signal(
        self, session: VISASession, line: constants.UtilityBusSignal
    ) -> StatusCode:
        """Assert or deassert the specified utility bus signal.

        Corresponds to viAssertUtilSignal function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        line : constants.UtilityBusSignal
            Specifies the utility bus signal to assert.

        Returns
        -------
```
