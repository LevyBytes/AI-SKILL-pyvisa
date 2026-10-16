# pyvisa.resources.TCPIPInstrument.write_ascii_values
Context: PyVISA pyvisa.resources.TCPIPInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](tcpip-instrument.md)

```text
write_ascii_values(
    message: str,
    values: Iterable[Any],
    converter: Literal['s', 'b', 'c', 'd', 'o', 'x', 'X', 'e', 'E', 'f', 'F', 'g', 'G'] | Callable[[str], Any] = 'f',
    separator: str | Callable[[Iterable[str]], str] = ',',
    termination: str | None = None,
    encoding: str | None = None,
)
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)
- [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)
- [None](https://docs.python.org/3/library/constants.html#None)

Write a string message, then append values formatted as ASCII data for the device.

The write_termination is always appended to it.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Header of the message to be sent.

- **values** (Sequence[Any]) – Data to be written to the device.

- **converter** (Union[[str](https://docs.python.org/3/library/stdtypes.html#str), Callable[[Any], [str](https://docs.python.org/3/library/stdtypes.html#str)]], optional) – String format code or callable used to convert each value. Defaults to f.

- **separator** (Union[[str](https://docs.python.org/3/library/stdtypes.html#str), Callable[[Iterable[[str](https://docs.python.org/3/library/stdtypes.html#str)]], [str](https://docs.python.org/3/library/stdtypes.html#str)]], optional) – str value or callable that combines all values into one str. When given a str, separator.join(values) is used. Defaults to comma.

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Optional write termination override. None uses write_termination, and the default is None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Optional encoding override for converting str to bytes. None uses encoding, and the default is None.

Returns:

Number of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

