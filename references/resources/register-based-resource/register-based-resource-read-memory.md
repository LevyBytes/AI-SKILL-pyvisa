# pyvisa.resources.RegisterBasedResource.read_memory
Context: PyVISA pyvisa.resources.RegisterBasedResource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](register-based-resource.md)

```text
read_memory(
    space: AddressSpace,
    offset: int,
    width: DataWidth,
    extended: bool = False,
) → int
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [bool](https://docs.python.org/3/library/functions.html#bool)

Read a value from the specified memory space and offset.

Parameters:

- **space** (constants.AddressSpace) – Specifies the address space from which to read.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Byte offset for the address or register being read.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Bits per element for the transfer.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits for the offset regardless of platform. Defaults to False.

Returns:

**data** – Data read from memory

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

