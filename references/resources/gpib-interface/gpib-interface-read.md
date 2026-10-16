# pyvisa.resources.GPIBInterface.read
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
read(termination: str | None = None, encoding: str | None = None) → str
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [None](https://docs.python.org/3/library/constants.html#None)

Read a text response from the device.

Reading ends when the device stops transmitting, such as by setting the relevant bus lines, or when the termination character sequence is found. Only the final character in the termination sequence actually stops the read, but the full sequence is checked against the end of the message; a mismatch causes a warning.

Parameters:

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Alternate termination character to apply. With None, read_termination supplies the value. Defaults to None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Alternate encoding for converting bytes to str. With None, encoding supplies the value. Defaults to None.

Returns:

Decoded message read from the instrument.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

