# pyvisa.resources.GPIBInterface.query_binary_values
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
query_binary_values(
    message: str,
    datatype: typing.Literal['s', 'b', 'B', 'h', 'H', 'i', 'I', 'l', 'L', 'q', 'Q', 'f', 'd'] = 'f',
    is_big_endian: bool = False,
    container: typing.Type | typing.Callable[[typing.Iterable], typing.Sequence] = <class 'list'>,
    delay: float | None = None,
    header_fmt: typing.Literal['ieee', 'hp', 'rs', 'empty'] = 'ieee',
    expect_termination: bool = True,
    data_points: int = 0,
    chunk_size: int | None = None,
    monitoring_interface: pyvisa.resources.messagebased.SupportsUpdate | None = None,
    length_before_block: int | None = None,
    raise_on_late_block: bool = False,
) → Sequence[int | float]
```

Type and source details:

- [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)
- [int](https://docs.python.org/3/library/functions.html#int)
- [float](https://docs.python.org/3/library/functions.html#float)

Ask the device for binary-formatted values and return the parsed values as an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Message that will be sent.

- **datatype** (BINARY_DATATYPES, optional) – Format string for one element. See the struct module. The default is ‘f’.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Selects big-endian rather than little-endian data order. Defaults to False.

- **container** (Union[Type, Callable[[Iterable], Sequence]], optional) – Container type for returned data. Valid choices include list, tuple, np.ndarray, and similar types. The default is list.

- **delay** (Optional[[float](https://docs.python.org/3/library/functions.html#float)], optional) – Seconds to wait between the write and read steps. With None, self.query_delay is used.

- **header_fmt** (util.BINARY_HEADERS, optional) – Header format placed before the data. Defaults to ‘ieee’.

- **expect_termination** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – When False, the expected binary block length excludes the final termination character (the read termination). Defaults to True.

- **data_points** ([int](https://docs.python.org/3/library/functions.html#int), optional) – Expected point count in the block. It is used only when the instrument does not provide that count. The value is converted to bytes from datatype. Defaults to 0.

- **chunk_size** ([int](https://docs.python.org/3/library/functions.html#int), optional) – Chunk size for reads from the device. Larger chunks can improve speed for large data transfers.

- **monitoring_interface** (SupportsUpdate Protocol, optional) – Progress monitor object whose update() method accepts the byte count already read. See the tqdm documentation for details on that progress bar package.

Returns:

Data returned by the device.

Return type:

Sequence[Union[[int](https://docs.python.org/3/library/functions.html#int), [float](https://docs.python.org/3/library/functions.html#float)]]

