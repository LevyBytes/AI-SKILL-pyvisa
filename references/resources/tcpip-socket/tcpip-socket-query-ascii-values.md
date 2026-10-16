# pyvisa.resources.TCPIPSocket.query_ascii_values
Context: PyVISA pyvisa.resources.TCPIPSocket; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](tcpip-socket.md)

```text
query_ascii_values(
    message: str,
    converter: typing.Literal['s', 'b', 'c', 'd', 'o', 'x', 'X', 'e', 'E', 'f', 'F', 'g', 'G'] | typing.Callable[[str], typing.Any] = 'f',
    separator: str | typing.Callable[[str], typing.Iterable[str]] = ',',
    container: typing.Type | typing.Callable[[typing.Iterable], typing.Sequence] = <class 'list'>,
    delay: float | None = None,
) → Sequence[Any]
```

Type and source details:

- [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)
- [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Query the device and parse returned ASCII values into an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **converter** (ASCII_CONVERTER, optional) – Str format of function to convert each value. Default to “f”.

- **separator** (Union[[str](https://docs.python.org/3/library/stdtypes.html#str), Callable[[[str](https://docs.python.org/3/library/stdtypes.html#str)], Iterable[[str](https://docs.python.org/3/library/stdtypes.html#str)]]]) – Use a str or callable to divide the returned data into elements. With a str, data.split(separator) is used. Default is “,”.

- **container** (Union[Type, Callable[[Iterable], Sequence]], optional) – Container type for returned data. Accepted examples include list, tuple, np.ndarray, and similar containers. Default is list.

- **delay** (Optional[[float](https://docs.python.org/3/library/functions.html#float)], optional) – Wait time in seconds between the write and read steps. If None, uses self.query_delay.

Returns:

Parsed data.

Return type:

Sequence

