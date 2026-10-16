# pyvisa.resources.PXIMemory.lock_context
Context: PyVISA pyvisa.resources.PXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-memory.md)

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

- **timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) - Millisecond timeout for waiting until the locking session unlocks the resource before reporting an error. If set to "default", self.timeout supplies the value.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) - With the default 'exclusive' setting, the lock is exclusive. Any other value is treated as the shared-lock access key, while None asks for a new shared access key.

Yields:

Optional[str] – The access_key if applicable.

