# pyvisa.resources.GPIBInterface.write
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)



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

The write_termination value is always appended.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Message that will be sent.

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Alternate termination character to apply. With None, write_termination supplies the value. Defaults to None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Alternate encoding for converting str to bytes. With None, encoding supplies the value. Defaults to None.

Returns:

Count of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

