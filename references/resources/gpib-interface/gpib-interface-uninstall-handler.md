# pyvisa.resources.GPIBInterface.uninstall_handler
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
uninstall_handler(
    event_type: EventType,
    handler: Callable[[VISASession, EventType, VISAEventContext, Any], None],
    user_handle=None,
) → None
```

Type and source details:

- [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)
- [VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [None](https://docs.python.org/3/library/constants.html#None)

Remove event handlers from this resource.

Parameters:

- **event_type** (constants.EventType) – Logical identifier for the event.

- **handler** (VISAHandler) – Handler function that the client application wants removed.

- **user_handle** (Any) – User handle that install_handler returned.

