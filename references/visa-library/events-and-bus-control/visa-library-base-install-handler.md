# pyvisa.highlevel.VisaLibraryBase.install_handler
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)



```text
install_handler(
    session: VISASession,
    event_type: EventType,
    handler: Callable[[VISASession, EventType, VISAEventContext, Any], None],
    user_handle: Any,
) → Tuple[Callable[[VISASession, EventType, VISAEventContext, Any], None], Any, Any, StatusCode]
```

Type and source details:

- [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)
- [VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [None](https://docs.python.org/3/library/constants.html#None)
- [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Install handlers for event callbacks.

Corresponds to viInstallHandler function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **event_type** (constants.EventType) – Logical event identifier.

- **handler** (VISAHandler) – Reference to a handler that a client application installs.

- **user_handle** (Any) – Application-supplied value used to identify handlers uniquely for one event type.

Returns:

- **handler** (VISAHandler) – Handler to be installed by a client application.

- converted_user_handle – User handle converted to match the underlying library. Use this handle form for later calls to the library.

- converted_handler – Converted version of the handler satisfying to backend library.

- **status_code** (StatusCode) – Return value of the library call

