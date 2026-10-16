# pyvisa.resources.VXIMemory.lock_context
Context: PyVISA pyvisa.resources.VXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-memory.md)

```text
lock_context(timeout: float | Literal['default'] = 'default', requested_key: str | None = 'exclusive') → Iterator[str | None]
```

Type and source details:

- [float](https://docs.python.org/3/library/functions.html#float)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [None](https://docs.python.org/3/library/constants.html#None)
- [Iterator](https://docs.python.org/3/library/typing.html#typing.Iterator)

A context that locks

Parameters:

- **timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) - Millisecond timeout for waiting until the locking session unlocks the resource; an error is returned when it expires. The default "default" uses self.timeout.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) - With the default 'exclusive', the lock is exclusive. Any other value is used as the shared-lock access key, while None creates a new shared access key.

Yields:

Optional[str] – The access_key if applicable.

