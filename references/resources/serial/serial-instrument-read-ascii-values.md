# pyvisa.resources.SerialInstrument.read_ascii_values
Context: PyVISA pyvisa.resources.SerialInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](serial-instrument.md)

```text
read_ascii_values(
    converter: typing.Literal['s', 'b', 'c', 'd', 'o', 'x', 'X', 'e', 'E', 'f', 'F', 'g', 'G'] | typing.Callable[[str], typing.Any] = 'f',
    separator: str | typing.Callable[[str], typing.Iterable[str]] = ',',
    container: typing.Type | typing.Callable[[typing.Iterable], typing.Sequence] = <class 'list'>,
) → Sequence
```

Type and source details:

- [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)

Read ASCII-format values from the device and return them as an iterable.

Parameters:

**converter** (ASCII_CONVERTER, optional) – String format code or callable used to convert each value. Defaults to f.

separatorUnion[str, Callable[[str], Iterable[str]]]

Separator policy for splitting returned data into individual elements. A str calls data.split(separator); the default is comma.

containerUnion[Type, Callable[[Iterable], Sequence]], optional

Container used for the parsed output, such as list, tuple, or np.ndarray. The default container is list.

Returns:

Parsed data.

Return type:

Sequence

