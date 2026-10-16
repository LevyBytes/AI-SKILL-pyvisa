# pyvisa.resources.Resource.lock
Context: PyVISA pyvisa.resources.Resource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](resource.md)

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

- **timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) – How long, in milliseconds, the resource should wait for the locking session to release it before reporting an error. The "default" value uses self.timeout.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Key from another session when this session should share that lock; use None to create a fresh shared access key.

Returns:

Returns a newly generated shared access key when requested_key is None; otherwise returns requested_key.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

