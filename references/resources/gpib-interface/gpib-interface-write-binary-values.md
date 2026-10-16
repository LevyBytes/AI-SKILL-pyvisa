# pyvisa.resources.GPIBInterface.write_binary_values
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

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

Write a string message followed by binary-formatted values to the device.

The write_termination value is always appended.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Header for the message that will be sent.

- **values** (Sequence[Any]) – Data that will be written to the device.

- **datatype** (util.BINARY_DATATYPES, optional) – Format string for one element. See the struct module.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Selects big-endian rather than little-endian data order.

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Alternate termination character to apply. With None, write_termination supplies the value. Defaults to None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Alternate encoding for converting str to bytes. With None, encoding supplies the value. Defaults to None.

- **header_fmt** (util.BINARY_HEADERS) – Header format placed before the data.

Returns:

Count of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

