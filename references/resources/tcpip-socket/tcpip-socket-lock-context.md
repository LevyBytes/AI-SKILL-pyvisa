# pyvisa.resources.TCPIPSocket.lock_context
Context: PyVISA pyvisa.resources.TCPIPSocket; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](tcpip-socket.md)



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

- **timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) – Time in milliseconds that the resource waits for the locking session to release it before an error is returned. The default is “default”, which uses self.timeout.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – With the default ‘exclusive’, the session takes an exclusive lock. For a shared lock, pass the access key, or pass None to create a new shared access key.

Yields:

Optional[str] – The access_key if applicable.

