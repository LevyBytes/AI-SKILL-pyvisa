# pyvisa.resources.USBRaw.write_ascii_values
Context: PyVISA pyvisa.resources.USBRaw; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](usb-raw.md)

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

Write a string message and append ASCII-formatted values to the device.

The write_termination is always appended to it.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Header of the message to be sent.

- **values** (Sequence[Any]) – Data to be written to the device.

- **converter** (Union[[str](https://docs.python.org/3/library/stdtypes.html#str), Callable[[Any], [str](https://docs.python.org/3/library/stdtypes.html#str)]], optional) – str formatting codes or a callable for converting each value. Defaults to “f”.

- **separator** (Union[[str](https://docs.python.org/3/library/stdtypes.html#str), Callable[[Iterable[[str](https://docs.python.org/3/library/stdtypes.html#str)]], [str](https://docs.python.org/3/library/stdtypes.html#str)]], optional) – str or callable that joins the values into one str. With a str, separator.join(values) is used. Defaults to ‘,’

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Character termination override. If None, write_termination supplies the value. Defaults to None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Encoding override for converting str to bytes. If None, encoding supplies the value. Defaults to None.

Returns:

Number of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

