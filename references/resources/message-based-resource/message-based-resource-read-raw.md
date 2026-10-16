# pyvisa.resources.MessageBasedResource.read_raw
Context: PyVISA pyvisa.resources.MessageBasedResource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](message-based-resource.md)

```text
read_raw(size: int | None = None) → bytes
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [None](https://docs.python.org/3/library/constants.html#None)
- [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

Read the unmodified string sent from the instrument to the computer.

In contrast to read(), no termination characters are stripped.

Parameters:

**size** (Optional[[int](https://docs.python.org/3/library/functions.html#int)], optional) – Chunk size for this read operation. None means the resource-wide value is used.

Returns:

Bytes read from the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

