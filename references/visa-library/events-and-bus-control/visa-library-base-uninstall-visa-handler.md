# pyvisa.highlevel.VisaLibraryBase.uninstall_visa_handler
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
uninstall_visa_handler(
    session: VISASession,
    event_type: EventType,
    handler: Callable[[VISASession, EventType, VISAEventContext, Any], None],
    user_handle: Any | None = None,
) → None
```

Type and source details:

- [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)
- [VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [None](https://docs.python.org/3/library/constants.html#None)
- [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Uninstalls handlers for events.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **event_type** (constants.EventType) – Logical event identifier.

- **handler** (VISAHandler) – Handler to be uninstalled by a client application.

- **user_handle** – The user handle returned by install_visa_handler.

