# pyvisa.resources.FirewireInstrument.install_handler
Context: PyVISA pyvisa.resources.FirewireInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](firewire-instrument.md)

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

Install callback handlers for events on this resource.

Parameters:

- **event_type** (constants.EventType) – Logical identifier for the event.

- **handler** (VISAHandler) – Handler function that the client application wants installed.

- **user_handle** – Application-supplied value used to identify handlers uniquely for an event type. Backends may restrict allowed values; see the backend install_visa_handler for details.

Returns:

User handle in the format expected by the backend. Use this handle representation when uninstalling a handler.

Return type:

Any

