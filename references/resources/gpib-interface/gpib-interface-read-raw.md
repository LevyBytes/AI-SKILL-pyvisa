# pyvisa.resources.GPIBInterface.read_raw
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
read_raw(size: int | None = None) → bytes
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [None](https://docs.python.org/3/library/constants.html#None)
- [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

Read the raw byte string sent from the instrument to the computer.

Unlike read(), this method leaves termination characters in place.

Parameters:

**size** (Optional[[int](https://docs.python.org/3/library/functions.html#int)], optional) – Chunk size used for the read. Defaults to None, which uses the resource-wide configured value.

Returns:

Bytes returned by the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

