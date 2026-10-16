# pyvisa.resources.MessageBasedResource.read_bytes
Context: PyVISA pyvisa.resources.MessageBasedResource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](message-based-resource.md)

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

Read a certain number of bytes from the instrument.

Parameters:

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – The number of bytes to read from the instrument.

- **chunk_size** (Optional[[int](https://docs.python.org/3/library/functions.html#int)], optional) – Chunk size for this read operation. If count > chunk_size, several low-level reads are used. None means the resource-wide value is used.

- **break_on_termchar** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Controls whether reading stops at a termination character instead of waiting for the message end. Defaults to False.

- **monitoring_interface** (SupportsUpdate Protocol, optional) – Progress monitor whose update() method receives the number of bytes read. The tqdm documentation describes a compatible progress-bar package.

Returns:

Bytes read from the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

