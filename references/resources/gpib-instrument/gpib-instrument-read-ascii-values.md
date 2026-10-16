# pyvisa.resources.GPIBInstrument.read_ascii_values
Context: PyVISA pyvisa.resources.GPIBInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-instrument.md)

```text
read_ascii_values(
    converter: typing.Literal['s', 'b', 'c', 'd', 'o', 'x', 'X', 'e', 'E', 'f', 'F', 'g', 'G'] | typing.Callable[[str], typing.Any] = 'f',
    separator: str | typing.Callable[[str], typing.Iterable[str]] = ',',
    container: typing.Type | typing.Callable[[typing.Iterable], typing.Sequence] = <class 'list'>,
) → Sequence
```

Type and source details:

- [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)

Read ASCII values from the device and return them as an iterable.

Parameters:

**converter** (ASCII_CONVERTER, optional) – Str format of function to convert each value. Default to “f”.

separatorUnion[str, Callable[[str], Iterable[str]]]

Use a str or callable to divide the returned data into elements. With a str, data.split(separator) is used. Default is “,”.

containerUnion[Type, Callable[[Iterable], Sequence]], optional

Container type for returned data. Accepted examples include list, tuple, np.ndarray, and similar containers. Default is list.

Returns:

Parsed data.

Return type:

Sequence

