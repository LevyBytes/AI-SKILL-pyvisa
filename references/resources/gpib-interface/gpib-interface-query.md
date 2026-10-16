# pyvisa.resources.GPIBInterface.query
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
query(message: str, delay: float | None = None) → str
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [float](https://docs.python.org/3/library/functions.html#float)
- [None](https://docs.python.org/3/library/constants.html#None)

Run write(message), then read(), as one query operation.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Message that will be sent.

- **delay** (Optional[[float](https://docs.python.org/3/library/functions.html#float)], optional) – Seconds to wait between the write and read steps. With None, self.query_delay is used.

Returns:

Response received from the device.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

