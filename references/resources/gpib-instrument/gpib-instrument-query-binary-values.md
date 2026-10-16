# pyvisa.resources.GPIBInstrument.query_binary_values
Context: PyVISA pyvisa.resources.GPIBInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-instrument.md)

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

Query the device and parse returned binary values into an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **datatype** (BINARY_DATATYPES, optional) – Format string for one element; see the struct module. Default is ‘f’.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Indicates whether the data use big endian or little endian order. Defaults to False.

- **container** (Union[Type, Callable[[Iterable], Sequence]], optional) – Container type for returned data. Accepted examples include list, tuple, np.ndarray, and similar containers. Default is list.

- **delay** (Optional[[float](https://docs.python.org/3/library/functions.html#float)], optional) – Wait time in seconds between the write and read steps. If None, uses self.query_delay.

- **header_fmt** (util.BINARY_HEADERS, optional) – Header format that prefixes the data. Defaults to ‘ieee’.

- **expect_termination** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – If False, the expected binary block length excludes the final termination character (the read termination). Defaults to True.

- **data_points** ([int](https://docs.python.org/3/library/functions.html#int), optional) – Expected number of points in the block. Use this only when the instrument does not report the value itself; PyVISA converts it to bytes from the datatype. Defaults to 0.

- **chunk_size** ([int](https://docs.python.org/3/library/functions.html#int), optional) – Chunk size used when reading from the device. Larger chunks can improve throughput for large data transfers.

- **monitoring_interface** (SupportsUpdate Protocol, optional) – Progress monitor object with update() method accepting the bytes-read count. See the tqdm documentation (a progress bar package) for details.

Returns:

Data read from the device.

Return type:

Sequence[Union[[int](https://docs.python.org/3/library/functions.html#int), [float](https://docs.python.org/3/library/functions.html#float)]]

