# pyvisa.resources.USBRaw.read_bytes
Context: PyVISA pyvisa.resources.USBRaw; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](usb-raw.md)

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

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to read from the instrument.

- **chunk_size** (Optional[[int](https://docs.python.org/3/library/functions.html#int)], optional) – Chunk size used for reading. If count > chunk_size, PyVISA performs multiple low-level operations. Defaults to None, meaning the resource-wide setting is used.

-
**break_on_termchar** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Stop reading when either a termination character appears or the message ends. Defaults to False.

- **monitoring_interface** (SupportsUpdate Protocol, optional) – Progress monitor object with update() method accepting the bytes-read count. See the tqdm documentation (a progress bar package) for details.

Returns:

Bytes read from the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

