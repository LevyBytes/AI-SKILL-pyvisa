# pyvisa.resources.PXIMemory.write_memory
Context: PyVISA pyvisa.resources.PXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-memory.md)

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

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) - Byte offset of the address or register to read from.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) - Bit width to read.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) - Use a 64 bits offset across platforms; by default False.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

