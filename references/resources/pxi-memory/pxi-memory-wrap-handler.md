# pyvisa.resources.PXIMemory.wrap_handler
Context: PyVISA pyvisa.resources.PXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-memory.md)

```text
wrap_handler(callable: Callable[[Resource, Event, Any], None]) → Callable[[VISASession, EventType, VISAEventContext, Any], None]
```

Type and source details:

- [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)
- [Resource, Event, [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [None](https://docs.python.org/3/library/constants.html#None)
- [VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Wrap an event handler to provide the signature expected by VISA.

Use this callable shape for the handler: handler(resource: Resource, event: Event, user_handle: Any) -> None.

Use the wrapped handler only for events raised by the same resource that wrapped it.

