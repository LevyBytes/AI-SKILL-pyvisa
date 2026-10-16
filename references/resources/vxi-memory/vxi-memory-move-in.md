# pyvisa.resources.VXIMemory.move_in
Context: PyVISA pyvisa.resources.VXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-memory.md)

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

Transfer a data block from the specified address space and offset into local memory.

Corresponds to viMoveIn\* functions of the VISA library.

Parameters:

- **space** (constants.AddressSpace) – Address space from which to move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) - Byte offset of the address or register that supplies the data.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) - Number of elements to transfer; each element uses the same data width as the source.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) - Bits read for each element.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) - Use platform-independent 64 bits offset behavior; by default False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (constants.StatusCode) – Return value of the library call.

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

