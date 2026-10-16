# pyvisa.resources.FirewireInstrument.lock
Context: PyVISA pyvisa.resources.FirewireInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](firewire-instrument.md)

```text
lock(timeout: float | Literal['default'] = 'default', requested_key: str | None = None) → str
```

Type and source details:

- [float](https://docs.python.org/3/library/functions.html#float)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [None](https://docs.python.org/3/library/constants.html#None)

Establish a shared lock on the resource.

Parameters:

- **timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) – Absolute wait time, in milliseconds, for the locking session to release the resource before an error is returned. Defaults to “default”, meaning self.timeout is used.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Access key from another session for sharing a lock, or None to create a new shared access key.

Returns:

New shared access key when requested_key is None; otherwise the requested_key value is returned.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

