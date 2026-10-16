# pyvisa.resources.USBInstrument.write
Context: PyVISA pyvisa.resources.USBInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](usb-instrument.md)

```text
write(
    message: str,
    termination: str | None = None,
    encoding: str | None = None,
) → int
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [None](https://docs.python.org/3/library/constants.html#None)
- [int](https://docs.python.org/3/library/functions.html#int)

Write a string message to the device.

The write_termination is always appended to it.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to be sent.

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Character termination override. If None, write_termination supplies the value. Defaults to None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Encoding override for converting str to bytes. If None, encoding supplies the value. Defaults to None.

Returns:

Number of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

