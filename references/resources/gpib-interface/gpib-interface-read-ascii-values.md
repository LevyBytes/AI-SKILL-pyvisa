# pyvisa.resources.GPIBInterface.read_ascii_values
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
read_ascii_values(
    converter: typing.Literal['s', 'b', 'c', 'd', 'o', 'x', 'X', 'e', 'E', 'f', 'F', 'g', 'G'] | typing.Callable[[str], typing.Any] = 'f',
    separator: str | typing.Callable[[str], typing.Iterable[str]] = ',',
    container: typing.Type | typing.Callable[[typing.Iterable], typing.Sequence] = <class 'list'>,
) → Sequence
```

Type and source details:

- [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)

Read ASCII-formatted values from the device and return the parsed values as an iterable.

Parameters:

**converter** (ASCII_CONVERTER, optional) – String format code or callable used for each value. The default is “f”.

separatorUnion[str, Callable[[str], Iterable[str]]]

String or callable used to divide the data into elements. When a str is supplied, parsing uses data.split(separator). The default is “,”.

containerUnion[Type, Callable[[Iterable], Sequence]], optional

Container type for returned data. Valid choices include list, tuple, np.ndarray, and similar types. The default is list.

Returns:

Parsed values.

Return type:

Sequence

