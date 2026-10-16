# pyvisa.resources.GPIBInterface.write_raw
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
write_raw(message: bytes) → int
```

Type and source details:

- [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)
- [int](https://docs.python.org/3/library/functions.html#int)

Write a bytes message to the device.

Parameters:

**message** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – Message that will be sent.

Returns:

Count of bytes written

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

