# pyvisa.highlevel.VisaLibraryBase

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md)

```python
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
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
