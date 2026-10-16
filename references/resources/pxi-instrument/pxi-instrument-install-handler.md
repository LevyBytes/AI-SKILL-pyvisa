# pyvisa.resources.PXIInstrument.install_handler
Context: PyVISA pyvisa.resources.PXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-instrument.md)

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

- **user_handle** - Application-provided value used to distinguish handlers for a given event type. Backend implementations may limit which values are accepted. See the backend install_visa_handler for additional details.

Returns:

User handle converted into a backend-friendly representation. Use this representation when unistalling a handler.

Return type:

Any

