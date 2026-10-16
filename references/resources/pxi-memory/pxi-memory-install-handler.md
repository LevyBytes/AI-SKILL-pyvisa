# pyvisa.resources.PXIMemory.install_handler
Context: PyVISA pyvisa.resources.PXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-memory.md)

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

- **user_handle** - Application-provided value for distinguishing handlers for a single event type. Backend implementations can restrict accepted values; see that backend's install_visa_handler details.

Returns:

Backend-friendly user handle form. Use this representation when uninstalling a handler.

Return type:

Any

