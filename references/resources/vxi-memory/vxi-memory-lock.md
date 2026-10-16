# pyvisa.resources.VXIMemory.lock
Context: PyVISA pyvisa.resources.VXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-memory.md)

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

- **timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) - Absolute wait, in milliseconds, before an error is returned while a resource is blocked by the locking session. Defaults to "default", which uses self.timeout.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) - Access key from another session for sharing its lock, or None to create a new shared access key.

Returns:

If requested_key is None, returns a new shared access key; otherwise returns requested_key unchanged.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

