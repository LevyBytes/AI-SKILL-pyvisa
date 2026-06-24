# Highlevel (part 2) (4)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

        session : VISASession
            Unique logical identifier to a session.

        Returns
        -------
        int
            Service request status byte
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def read_to_file(
self, session: VISASession, filename: str, count: int
) -> Tuple[int, StatusCode]:
"""Read data synchronously, and store the transferred data in a file.

        Corresponds to viReadToFile function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        filename : str
            Name of file to which data will be written.
        count : int
            Number of bytes to be read.

        Returns
        -------
        int
            Number of bytes actually transferred
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def set_attribute(
self,
session: VISASession,
attribute: constants.ResourceAttribute,
attribute_state: Any,
) -> StatusCode:
"""Set the state of an attribute.

        Corresponds to viSetAttribute function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        attribute : constants.ResourceAttribute
            Attribute for which the state is to be modified.
        attribute_state : Any
            The state of the attribute to be set for the specified object.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def set_buffer(
self, session: VISASession, mask: constants.BufferType, size: int
) -> StatusCode:
"""Sets the communication buffer size used for formatted I/O and/or low-level I/O.

        Corresponds to viSetBuf function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        mask : constants.BufferType
            Specifies the type of buffer.
        size : int
            The size to be set for the specified buffer(s).

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def status_description(
self, session: VISASession, status: StatusCode
) -> Tuple[str, StatusCode]:
"""Return text that explains the supplied status code in a user-readable form.

        Corresponds to viStatusDesc function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        status : StatusCode
            Status code to interpret.

        Returns
        -------
        str
            User-readable string interpretation of the status code.
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def terminate(
self, session: VISASession, degree: None, job_id: VISAJobID
) -> StatusCode:
"""Request a VISA session to terminate normal execution of an operation.

        Corresponds to viTerminate function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        degree : None
            Not used in this version of the VISA specification.
        job_id : VISAJobId
            Specifies an operation identifier. If a user passes None as the
            job_id value to viTerminate(), a VISA implementation should abort
            any calls in the current process executing on the specified vi.
            Any call that is terminated this way should return VI_ERROR_ABORT.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def uninstall_handler(
self,
session: VISASession,
event_type: constants.EventType,
handler: VISAHandler,
user_handle: Any = None,
) -> StatusCode:
"""Uninstall handlers for events.

        Corresponds to viUninstallHandler function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Logical event identifier.
        handler : VISAHandler
            Handler to be uninstalled by a client application.
        user_handle:
            A value specified by an application that can be used for
            identifying handlers uniquely in a session for an event.
            The modified value of the user_handle as returned by install_handler
            should be used instead of the original value.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def unlock(self, session: VISASession) -> StatusCode:
"""Relinquish a lock for the specified resource.

        Corresponds to viUnlock function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def unmap_address(self, session: VISASession) -> StatusCode:
"""Unmap memory space previously mapped by map_address().

        Corresponds to viUnmapAddress function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def unmap_trigger(
self,
session: VISASession,
trigger_source: constants.InputTriggerLine,
trigger_destination: constants.OutputTriggerLine,
) -> StatusCode:
"""Remove an existing trigger mapping from a source line to a destination line.

        Corresponds to viUnmapTrigger function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        trigger_source : constants.InputTriggerLine
            Source line used in previous map.
        trigger_destination : constants.OutputTriggerLine
            Destination line used in previous map.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def usb_control_in(
self,
session: VISASession,
request_type_bitmap_field: int,
request_id: int,
request_value: int,
index: int,
length: int = 0,
) -> Tuple[bytes, StatusCode]:
"""Perform a USB control pipe transfer from the device.

        Corresponds to viUsbControlIn function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        request_type_bitmap_field : int
            bmRequestType parameter of the setup stage of a USB control transfer.
        request_id : int
            bRequest parameter of the setup stage of a USB control transfer.
        request_value : int
            wValue parameter of the setup stage of a USB control transfer.
        index : int
            wIndex parameter of the setup stage of a USB control transfer.
            This is usually the index of the interface or endpoint.
        length : int, optional
            wLength parameter of the setup stage of a USB control transfer.
            This value also specifies the size of the data buffer to receive
            the data from the optional data stage of the control transfer.

        Returns
        -------
        bytes
            The data buffer that receives the data from the optional data stage
            of the control transfer
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def usb_control_out(
self,
session: VISASession,
request_type_bitmap_field: int,
request_id: int,
request_value: int,
index: int,
data: bytes = b"",
) -> StatusCode:
"""Perform a USB control pipe transfer to the device.

        Corresponds to viUsbControlOut function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        request_type_bitmap_field : int
            bmRequestType parameter of the setup stage of a USB control transfer.
        request_id : int
            bRequest parameter of the setup stage of a USB control transfer.
        request_value : int
            wValue parameter of the setup stage of a USB control transfer.
        index : int
            wIndex parameter of the setup stage of a USB control transfer.
            This is usually the index of the interface or endpoint.
        data : bytes, optional
            Data buffer used for the optional data stage of the control
            transfer.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def vxi_command_query(
self, session: VISASession, mode: constants.VXICommands, command: int
) -> Tuple[int, StatusCode]:
"""Send a miscellaneous command or query to the device and/or return the response from a previous query.

        Corresponds to viVxiCommandQuery function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        mode : constants.VXICommands
            Specifies whether to issue a command and/or retrieve a response.
        command : int
            The miscellaneous command to send.

        Returns
        -------
        int
            The response retrieved from the device
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def wait_on_event(
self, session: VISASession, in_event_type: constants.EventType, timeout: int
) -> Tuple[constants.EventType, VISAEventContext, StatusCode]:
"""Wait for an occurrence of the specified event for a given session.

        Corresponds to viWaitOnEvent function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        in_event_type : constants.EventType
            Logical identifier of the event(s) to wait for.
        timeout : int
            Absolute time period in time units that the resource shall wait for
            a specified event to occur before returning the time elapsed error.
            The time unit is in milliseconds.

        Returns
        -------
        constants.EventType
            Logical identifier of the event actually received
        VISAEventContext
            A handle specifying the unique occurrence of an event
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def write(self, session: VISASession, data: bytes) -> Tuple[int, StatusCode]:
"""Write data to device or interface synchronously.

        Corresponds to viWrite function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        data : bytes
            Data to be written.

        Returns
        -------
        int
            Number of bytes actually transferred
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def write_asynchronously(
self, session: VISASession, data: bytes
) -> Tuple[VISAJobID, StatusCode]:
"""Write data to device or interface asynchronously.

        Corresponds to viWriteAsync function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        data : bytes
            Data to be written.

        Returns
        -------
        VISAJobID
            Job ID of this asynchronous write operation
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def write_from_file(
self, session: VISASession, filename: str, count: int
) -> Tuple[int, StatusCode]:
"""Take data from a file and write it out synchronously.

        Corresponds to viWriteFromFile function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        filename : str
            Name of file from which data will be read.
        count : int
            Number of bytes to be written.

        Returns
        -------
        int
            Number of bytes actually transferred
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

def list_backends() -> List[str]:
"""Return installed backends.

    Backends are installed python packages named pyvisa_<something> where <something>
    is the name of the backend.

    """
    return ["ivi"] + [
        name[7:]
        for (loader, name, ispkg) in pkgutil.iter_modules()
        if (name.startswith("pyvisa_") or name.startswith("pyvisa-"))
        and not name.endswith("-script")
    ]

#: Maps backend name to VisaLibraryBase derived class
\WRAPPERS: Dict[str, Type[VisaLibraryBase]] = {}

class PyVISAModule(ModuleType):
WRAPPER_CLASS: Type[VisaLibraryBase]

def get_wrapper_class(backend_name: str) -> Type[VisaLibraryBase]:
"""Return the WRAPPER_CLASS for a given backend."""
try:
return \WRAPPERS[backend_name]
except KeyError:
if backend_name == "ivi":
from .ctwrapper import IVIVisaLibrary

            WRAPPERS["ivi"] = IVIVisaLibrary
            return IVIVisaLibrary

    pkg: PyVISAModule
    try:
        pkg = cast(PyVISAModule, import_module("pyvisa_" + backend_name))
        WRAPPERS[backend_name] = cls = pkg.WRAPPER_CLASS
        return cls
    except ImportError:
        raise ValueError("Wrapper not found: No package named pyvisa_%s" % backend_name)

def \get_default_wrapper() -> str:
"""Return an available default VISA wrapper as a string ('ivi' or 'py').

    Prefer IVI when its binary is present; otherwise check pyvisa-py.

    'ni' VISA wrapper is NOT used since version > 1.10.0
    and will be removed in 1.12

    Raises
    ------
    ValueError
        If no backend can be found

    """

    from .ctwrapper import IVIVisaLibrary

    ivi_binary_found = bool(IVIVisaLibrary.get_library_paths())
    if ivi_binary_found:
        logger.debug("The IVI implementation available")
        return "ivi"
    else:
        logger.debug("Did not find IVI binary")

    try:
        get_wrapper_class("py")  # check for pyvisa-py availability
        logger.debug("pyvisa-py is available.")
        return "py"
    except ValueError:
        logger.debug("Did not find pyvisa-py package")
    raise ValueError(
        "No VISA implementation was found. Install the IVI binary or pyvisa-py."
    )

def open_visa_library(specification: str = "") -> VisaLibraryBase:
"""Helper function to create a VISA library wrapper.

    In general, you should not use the function directly. The VISA library
    wrapper will be created automatically when you create a ResourceManager object.

    Parameters
    ----------
    specification : str, optional
        The specification contains 2 parts split at '@', ex: path/visa.dll@ivi
        The second part names the backend (ivi, py, ...), while the first part
        is passed to the library object. For the ivi backend it should be the
        path to the VISA library.
        Either part may be omitted. When the second part is absent, the system
        uses the ivi backend if available, or the pyvisa-py backend if the
        first part is also omitted.

    """

    if not specification:
        logger.debug("No visa library specified, trying to find alternatives.")
        try:
            specification = os.environ["PYVISA_LIBRARY"]
        except KeyError:
            logger.debug("Environment variable PYVISA_LIBRARY is unset.")

    wrapper: Optional[str]
    try:
        argument, wrapper = specification.rsplit("@", 1)
    except ValueError:
        argument = specification
        wrapper = None  # Flag that we need a fallback, but avoid nested exceptions
    if wrapper is None:
        if argument:  # some filename given
            wrapper = "ivi"
        else:
            wrapper = get_default_wrapper()

    cls = get_wrapper_class(wrapper)

    try:
        return cls(argument)
    except Exception as e:
        logger.debug("Unable to open VISA wrapper %s using %s\n%s", cls, str(argument), e)
        raise

[docs]
class ResourceManager(object):
"""VISA Resource Manager."""

    #: Maps (Interface Type, Resource Class) to Python class encapsulating that resource.
    resource_classes: ClassVar[
        Dict[Tuple[constants.InterfaceType, str], Type["Resource"]]
    ] = {}

    #: Session handler for the resource manager.
    session: Optional[VISARMSession] = None

    #: Reference to the VISA library used by the ResourceManager
    visalib: VisaLibraryBase

    #: Resources created by this manager to allow closing them when the manager is closed
    created_resources: WeakSet

    #: Handler for atexit using a weakref to close
    atexit_handler: Callable

    @classmethod
    def register_resource_class(
        cls,
        interface_type: constants.InterfaceType,
        resource_class: str,
        python_class: Type["Resource"],
    ) -> None:
        """Register a class for a specific interface type, resource class pair.

        Parameters
        ----------
        interface_type : constants.InterfaceType
            Interface type for which to use the provided class.
        resource_class : str
            Resource class (INSTR, INTFC, ...)  for which to use the provided class.
        python_class : Type[Resource]
            Subclass of ``Resource`` to use when opening a resource matching the
            specified interface type and resource class.

        """
        if (interface_type, resource_class) in cls.resource_classes:
            logger.warning(
                "%s is already registered in the ResourceManager. "
                "Overwriting with %s" % ((interface_type, resource_class), python_class)
            )

        # If the class already has this attribute, it means that a parent class
        # was registered first. We need to copy the current set and extend it.
        attrs: Set[Type[attributes.Attribute]] = copy.copy(
            getattr(python_class, "visa_attributes_classes", set())
        )

        for attr in chain(
            attributes.AttributesPerResource[(interface_type, resource_class)],
            attributes.AttributesPerResource[attributes.AllSessionTypes],
        ):
            attrs.add(attr)
            # Error on non-properly set descriptor (this ensures that we are
            # consistent)
            if attr.py_name != "" and not hasattr(python_class, attr.py_name):
                raise TypeError(
                    "%s was expected to have a visa attribute %s"
                    % (python_class, attr.py_name)
                )

        setattr(python_class, "visa_attributes_classes", attrs)

        cls.resource_classes[(interface_type, resource_class)] = python_class

    def __new__(
        cls: Type["ResourceManager"], visa_library: Union[str, VisaLibraryBase] = ""
    ) -> "ResourceManager":
        """Create a new resource manager tied to the specified VISA library.

        Parameters
        ----------
        visa_library : Union[str, VisaLibraryBase]
            Either a fully initialized VisaLibraryBase subclass instance or
            a str specification (see open_visa_library for the format).

        """
        if not isinstance(visa_library, VisaLibraryBase):
            visa_library = open_visa_library(visa_library)

        if visa_library.resource_manager is not None:
            obj = visa_library.resource_manager
            logger.debug("Reusing ResourceManager with session %s", obj.session)
            return obj

        obj = super(ResourceManager, cls).__new__(cls)

        obj.session, err = visa_library.open_default_resource_manager()

        obj.visalib = visa_library
        obj.visalib.resource_manager = obj
        obj.created_resources = WeakSet()

        # Register an atexit handler to ensure the Resource Manager is properly
        # closed.
        close_ref = WeakMethod(obj.close)  # type: ignore

        def call_close():
            try:
                meth = close_ref()
                if meth:
                    meth()
            except Exception:
                # Suppress exceptions during exit
                logger.warning(
                    "Exception suppressed while closing a ResourceManager at system exit",
                    exc_info=True,
                )

        atexit.register(call_close)
        obj.atexit_handler = call_close  # type: ignore

        logger.debug("Created ResourceManager with session %s", obj.session)
        return obj

    @property
    def session(self) -> VISARMSession:
        """Resource Manager session handle.

        Raises
        ------
        errors.InvalidSession
            Raised if the session is closed.

        """
        if self.session is None:
            raise errors.InvalidSession()
        return self.session

    @session.setter
    def session(self, value: Optional[VISARMSession]) -> None:
        self.session = value

    def __str__(self) -> str:
        return "Resource Manager of %s" % self.visalib

    def __repr__(self) -> str:
        return "<ResourceManager(%r)>" % self.visalib

    def __del__(self) -> None:
        if self.session is not None:
            self.close()

    def ignore_warning(self, *warnings_constants: StatusCode) -> ContextManager:
        """Ignoring warnings context manager for the current resource.

        Parameters
        ----------
        warnings_constants : StatusCode
            Constants identifying the warnings to ignore.

        """
        return self.visalib.ignore_warning(self.session, *warnings_constants)

    @property
    def last_status(self) -> StatusCode:
        """Last status code returned for an operation with this Resource Manager."""
        return self.visalib.get_last_status_in_session(self.session)

[docs]
def close(self) -> None:
"""Close the resource manager session.

        Notes
        -----
        Since the resource manager session is shared between instances
        this will also terminate connections obtained from other
        ResourceManager instances.

        """
        atexit.unregister(self.atexit_handler)
        try:
            logger.debug("Closing ResourceManager (session: %s)", self.session)
            # Cleanly close all resources when closing the manager.
            for resource in self.created_resources:
                resource.close()
            self.visalib.close(self.session)
            # mypy don't get that we can set a value we cannot get
            self.session = None  # type: ignore
            self.visalib.resource_manager = None
        except errors.InvalidSession:
            pass

[docs]
def list_resources(self, query: str = "?\*::INSTR") -> Tuple[str, ...]:
r"""Return a tuple of all connected devices matching query.

        Notes
        -----
        The query uses the VISA Resource Regular Expression syntax - which is
