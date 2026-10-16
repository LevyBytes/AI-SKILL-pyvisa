# pyvisa.resources.VXIBackplane.lock_context
Context: PyVISA pyvisa.resources.VXIBackplane; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-backplane.md)

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

- **timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) - Time in milliseconds that the resource waits for the locking session to unlock it before an error is returned. The "default" value means self.timeout is used.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) - With the default of 'exclusive', the lock is exclusive. Otherwise, pass the shared-lock access key, or use None to generate a new shared access key.

Yields:

Optional[str] – The access_key if applicable.

