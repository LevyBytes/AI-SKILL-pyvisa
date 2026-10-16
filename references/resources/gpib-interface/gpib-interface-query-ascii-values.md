# pyvisa.resources.GPIBInterface.query_ascii_values
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

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

Ask the device for ASCII-formatted values and return the parsed values as an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Message that will be sent.

- **converter** (ASCII_CONVERTER, optional) – String format code or callable used for each value. The default is “f”.

- **separator** (Union[[str](https://docs.python.org/3/library/stdtypes.html#str), Callable[[[str](https://docs.python.org/3/library/stdtypes.html#str)], Iterable[[str](https://docs.python.org/3/library/stdtypes.html#str)]]]) – String or callable used to divide the data into elements. When a str is supplied, parsing uses data.split(separator). The default is “,”.

- **container** (Union[Type, Callable[[Iterable], Sequence]], optional) – Container type for returned data. Valid choices include list, tuple, np.ndarray, and similar types. The default is list.

- **delay** (Optional[[float](https://docs.python.org/3/library/functions.html#float)], optional) – Seconds to wait between the write and read steps. With None, self.query_delay is used.

Returns:

Parsed values.

Return type:

Sequence

