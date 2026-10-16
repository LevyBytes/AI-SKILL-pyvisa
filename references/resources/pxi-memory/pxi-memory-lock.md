# pyvisa.resources.PXIMemory.lock
Context: PyVISA pyvisa.resources.PXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-memory.md)

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

- **timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) - Time, in milliseconds, to wait for the locking session to release the resource before an error is returned. The default value "default" uses self.timeout.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) - Access key from another session that this session should use to share a lock, or None to create a fresh shared access key.

Returns:

Returns a newly generated shared access key when requested_key is None; otherwise returns requested_key unchanged.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

