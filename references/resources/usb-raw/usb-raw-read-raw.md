# pyvisa.resources.USBRaw.read_raw
Context: PyVISA pyvisa.resources.USBRaw; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](usb-raw.md)



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

**size** (Optional[[int](https://docs.python.org/3/library/functions.html#int)], optional) – Chunk size used for reading. Defaults to None, meaning the resource-wide setting is used.

Returns:

Bytes read from the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

