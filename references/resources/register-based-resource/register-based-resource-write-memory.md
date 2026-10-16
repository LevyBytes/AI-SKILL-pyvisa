# pyvisa.resources.RegisterBasedResource.write_memory
Context: PyVISA pyvisa.resources.RegisterBasedResource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](register-based-resource.md)

```text
write_memory(
    space: AddressSpace,
    offset: int,
    data: int,
    width: DataWidth,
    extended: bool = False,
) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Write a value to the specified memory space and offset.

Parameters:

- **space** (constants.AddressSpace) – Specifies the address space.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Byte offset for the address or register being read.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Bits per element for the transfer.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits for the offset regardless of platform. Defaults to False.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

