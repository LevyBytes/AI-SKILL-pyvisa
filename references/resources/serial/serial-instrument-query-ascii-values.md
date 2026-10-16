# pyvisa.resources.SerialInstrument.query_ascii_values
Context: PyVISA pyvisa.resources.SerialInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](serial-instrument.md)

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

Query the device and return parsed ASCII-format values as an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **converter** (ASCII_CONVERTER, optional) – String format code or callable used to convert each value. Defaults to f.

- **separator** (Union[[str](https://docs.python.org/3/library/stdtypes.html#str), Callable[[[str](https://docs.python.org/3/library/stdtypes.html#str)], Iterable[[str](https://docs.python.org/3/library/stdtypes.html#str)]]]) – Separator policy for converting the returned text into elements. A str is passed to data.split(separator); the default is comma.

- **container** (Union[Type, Callable[[Iterable], Sequence]], optional) – Container used for the parsed output, such as list, tuple, or np.ndarray. The default container is list.

- **delay** (Optional[[float](https://docs.python.org/3/library/functions.html#float)], optional) – Seconds to pause between the write phase and the read phase. None uses self.query_delay.

Returns:

Parsed data.

Return type:

Sequence

