# pyvisa.resources.GPIBInterface.read_bytes
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
read_bytes(
    count: int,
    chunk_size: int | None = None,
    break_on_termchar: bool = False,
    monitoring_interface: SupportsUpdate | None = None,
) → bytes
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [None](https://docs.python.org/3/library/constants.html#None)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

Read a requested byte count from the instrument.

Parameters:

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to read from the instrument.

- **chunk_size** (Optional[[int](https://docs.python.org/3/library/functions.html#int)], optional) – Chunk size used for the read. If count > chunk_size, multiple low-level operations are performed. Defaults to None, which uses the resource-wide configured value.

- **break_on_termchar** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Controls whether reading stops on a termination character or only at message end. Defaults to False.

- **monitoring_interface** (SupportsUpdate Protocol, optional) – Progress monitor object whose update() method accepts the byte count already read. See the tqdm documentation for details on that progress bar package.

Returns:

Bytes returned by the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

