# pyvisa.resources.SerialInstrument.query_binary_values
Context: PyVISA pyvisa.resources.SerialInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](serial-instrument.md)

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

Query the device and return parsed binary-format values as an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **datatype** (BINARY_DATATYPES, optional) – Single-element format string; see the struct module. The default is f.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Are the data in big or little endian order. Defaults to False.

- **container** (Union[Type, Callable[[Iterable], Sequence]], optional) – Container used for the parsed output, such as list, tuple, or np.ndarray. The default container is list.

-
**delay** (Optional[[float](https://docs.python.org/3/library/functions.html#float)], optional) – Seconds to pause between the write phase and the read phase. None uses self.query_delay.

- **header_fmt** (util.BINARY_HEADERS, optional) – Format of the header prefixing the data. Defaults to ‘ieee’.

- **expect_termination** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – False means the calculated binary block length omits the final termination character, which is the read termination. Defaults to True.

- **data_points** ([int](https://docs.python.org/3/library/functions.html#int), optional) – Expected point count for blocks whose instrument does not provide one. The value is converted to bytes from the datatype. Defaults to 0.

- **chunk_size** ([int](https://docs.python.org/3/library/functions.html#int), optional) – Chunk size used while reading from the device; larger chunks can improve throughput for large data transfers.

- **monitoring_interface** (SupportsUpdate Protocol, optional) – Progress monitor whose update() method receives the number of bytes read. The tqdm documentation describes a compatible progress-bar package.

Returns:

Data read from the device.

Return type:

Sequence[Union[[int](https://docs.python.org/3/library/functions.html#int), [float](https://docs.python.org/3/library/functions.html#float)]]

