# pyvisa.resources.MessageBasedResource.write
Context: PyVISA pyvisa.resources.MessageBasedResource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](message-based-resource.md)

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

- **termination** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Optional write termination override. None uses write_termination, and the default is None.

- **encoding** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Optional encoding override for converting str to bytes. None uses encoding, and the default is None.

Returns:

Number of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

