# pyvisa.resources.FirewireInstrument.lock_context
Context: PyVISA pyvisa.resources.FirewireInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](firewire-instrument.md)

```text
lock_context(timeout: float | Literal['default'] = 'default', requested_key: str | None = 'exclusive') → Iterator[str | None]
```

Type and source details:

- [float](https://docs.python.org/3/library/functions.html#float)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [None](https://docs.python.org/3/library/constants.html#None)
- [Iterator](https://docs.python.org/3/library/typing.html#typing.Iterator)

Context manager that acquires a lock.

Parameters:

- **timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) – Absolute wait time, in milliseconds, for the locking session to release the resource before an error is returned. Defaults to “default”, meaning self.timeout is used.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – With the default ‘exclusive’, an exclusive lock is used. Otherwise, pass the shared-lock access key, or None to create a new shared access key.

Yields:

Optional[str] – The access_key, when one applies.

