# pyvisa.resources.PXIInstrument.lock
Context: PyVISA pyvisa.resources.PXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-instrument.md)

```text
lock(timeout: float | Literal['default'] = 'default', requested_key: str | None = None) → str
```

Type and source details:

- [float](https://docs.python.org/3/library/functions.html#float)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [None](https://docs.python.org/3/library/constants.html#None)

Establish a shared lock to the resource.

Parameters:

- **timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) - Maximum wait, in milliseconds, for a locked resource to become available before an error is returned. Defaults to default, meaning self.timeout is used.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) - Access key from another session that this session should share a lock with, or None to create a new shared access key.

Returns:

Returns a new shared access key when requested_key is None; otherwise returns the requested_key value unchanged.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

