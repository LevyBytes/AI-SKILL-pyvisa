# pyvisa.resources.VXIInstrument.install_handler
Context: PyVISA pyvisa.resources.VXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-instrument.md)

```text
install_handler(
    event_type: EventType,
    handler: Callable[[VISASession, EventType, VISAEventContext, Any], None],
    user_handle=None,
) → Any
```

Type and source details:

- [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)
- [VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [None](https://docs.python.org/3/library/constants.html#None)
- [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Install handlers for event callbacks in this resource.

Parameters:

- **event_type** (constants.EventType) – Logical event identifier.

- **handler** (VISAHandler) – Handler function to be installed by a client application.

- **user_handle** - Application-provided value for uniquely identifying handlers for an event type. Backend implementations can restrict which values are valid; see the backend install_visa_handler for details.

Returns:

User handle converted into the backend-friendly representation. Use this representation when removing a handler.

Return type:

Any

