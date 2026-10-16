# pyvisa.resources.USBRaw.read
Context: PyVISA pyvisa.resources.USBRaw; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](usb-raw.md)

```text
read(termination: str | None = None, encoding: str | None = None) → str
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [None](https://docs.python.org/3/library/constants.html#None)

Read a string from the device.

Reading ends when the device stops transmitting (for example by setting the relevant bus lines) or when the termination character sequence is found. Only the final character of the termination sequence actually stops the read; the complete sequence is still checked against the end of the read string message, and a warning is emitted if it differs.

Parameters:

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Character termination override. If None, read_termination supplies the value. Defaults to None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Encoding override for decoding bytes to str. If None, encoding supplies the value. Defaults to None.

Returns:

Message read from the instrument and decoded.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

