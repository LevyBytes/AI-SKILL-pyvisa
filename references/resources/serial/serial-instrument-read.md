# pyvisa.resources.SerialInstrument.read
Context: PyVISA pyvisa.resources.SerialInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](serial-instrument.md)

```text
read(termination: str | None = None, encoding: str | None = None) → str
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [None](https://docs.python.org/3/library/constants.html#None)

Read a string from the device.

Reading ends when the device stops sending, such as by setting the relevant bus lines, or when the termination-character sequence is detected. Only the final termination character controls the stop condition, but PyVISA still compares the complete sequence with the end of the read string message and warns if they differ.

Parameters:

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Optional termination override. None falls back to read_termination, and the default is None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Optional decoding override for converting bytes to str. None uses encoding, and the default is None.

Returns:

Message read from the instrument and decoded.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

