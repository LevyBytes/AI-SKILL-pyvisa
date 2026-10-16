# pyvisa.resources.RegisterBasedResource.move_in
Context: PyVISA pyvisa.resources.RegisterBasedResource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](register-based-resource.md)

```text
move_in(
    space: AddressSpace,
    offset: int,
    length: int,
    width: DataWidth,
    extended: bool = False,
) → List[int]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [List](https://docs.python.org/3/library/typing.html#typing.List)

Copy a block from the specified address space and offset into local memory.

Corresponds to viMoveIn\* functions of the VISA library.

Parameters:

- **space** (constants.AddressSpace) – Address space from which to move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Byte offset for the address or register being read.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Element count to transfer; each element uses the same data width as the source.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Bits per element for the transfer.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits for the offset regardless of platform. Defaults to False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (constants.StatusCode) – Return value of the library call.

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

