# pyvisa.resources.GPIBInterface.write_ascii_values
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

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

Write a string message followed by ASCII-formatted values to the device.

The write_termination value is always appended.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Header for the message that will be sent.

- **values** (Sequence[Any]) – Data that will be written to the device.

- **converter** (Union[[str](https://docs.python.org/3/library/stdtypes.html#str), Callable[[Any], [str](https://docs.python.org/3/library/stdtypes.html#str)]], optional) – String formatting code or callable used to convert each value. Defaults to “f”.

- **separator** (Union[[str](https://docs.python.org/3/library/stdtypes.html#str), Callable[[Iterable[[str](https://docs.python.org/3/library/stdtypes.html#str)]], [str](https://docs.python.org/3/library/stdtypes.html#str)]], optional) - A str, or a callable, that turns the values into one str. With a str value, separator.join(values) performs the merge. Defaults to ','

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Alternate termination character to apply. With None, write_termination supplies the value. Defaults to None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Alternate encoding for converting str to bytes. With None, encoding supplies the value. Defaults to None.

Returns:

Count of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

