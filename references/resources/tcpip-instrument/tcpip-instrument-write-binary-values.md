# pyvisa.resources.TCPIPInstrument.write_binary_values
Context: PyVISA pyvisa.resources.TCPIPInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](tcpip-instrument.md)

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

Write a string message and then append values encoded in binary format for the device.

The write_termination is always appended to it.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The header of the message to be sent.

- **values** (Sequence[Any]) – Data to be written to the device.

- **datatype** (util.BINARY_DATATYPES, optional) – The format string for a single element. See struct module.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Are the data in big or little endian order.

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Optional write termination override. None uses write_termination, and the default is None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Optional encoding override for converting str to bytes. None uses encoding, and the default is None.

- **header_fmt** (util.BINARY_HEADERS) – Format of the header prefixing the data.

Returns:

Number of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

