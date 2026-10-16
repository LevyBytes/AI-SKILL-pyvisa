# pyvisa.resources.GPIBInterface.send_command
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
send_command(data: bytes) → Tuple[int, StatusCode]
```

Type and source details:

- [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Write GPIB command bytes to the bus.

This maps to the VISA library viGpibCommand function.

Parameters:

**data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – Command bytes to write.

Returns:

- int – Count of bytes written

- constants.StatusCode – Status returned by the library call.

