# pyvisa.resources.GPIBInstrument.query
Context: PyVISA pyvisa.resources.GPIBInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-instrument.md)

```text
query(message: str, delay: float | None = None) → str
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [float](https://docs.python.org/3/library/functions.html#float)
- [None](https://docs.python.org/3/library/constants.html#None)

A combination of write(message) and read()

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **delay** (Optional[[float](https://docs.python.org/3/library/functions.html#float)], optional) – Wait time in seconds between the write and read steps. If None, uses self.query_delay.

Returns:

Answer from the device.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

