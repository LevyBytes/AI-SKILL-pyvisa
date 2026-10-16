# pyvisa.resources.TCPIPSocket.write_binary_values
Context: PyVISA pyvisa.resources.TCPIPSocket; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](tcpip-socket.md)

```text
write_binary_values(
    message: str,
    values: Sequence[Any],
    datatype: Literal['s', 'b', 'B', 'h', 'H', 'i', 'I', 'l', 'L', 'q', 'Q', 'f', 'd'] = 'f',
    is_big_endian: bool = False,
    termination: str | None = None,
    encoding: str | None = None,
    header_fmt: Literal['ieee', 'hp', 'rs', 'empty'] = 'ieee',
)
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)
- [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [None](https://docs.python.org/3/library/constants.html#None)

Write a string message and append binary-formatted values to the device.

The write_termination is always appended to it.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The header of the message to be sent.

- **values** (Sequence[Any]) – Data to be written to the device.

- **datatype** (util.BINARY_DATATYPES, optional) – Format string for one element; see the struct module.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Indicates whether the data use big endian or little endian order.

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Character termination override. If None, write_termination supplies the value. Defaults to None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Encoding override for converting str to bytes. If None, encoding supplies the value. Defaults to None.

- **header_fmt** (util.BINARY_HEADERS) – Header format that prefixes the data.

Returns:

Number of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

