# pyvisa.resources.VXIInstrument.lock
Context: PyVISA pyvisa.resources.VXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-instrument.md)

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

- **timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) - Maximum wait, in milliseconds, for the locking session to release the resource before an error is returned. The "default" value uses self.timeout.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) - Access key from another session when this session should share that lock, or None to create a new shared access key.

Returns:

If requested_key is None, returns a new shared access key; otherwise returns the requested_key value unchanged.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

