# pyvisa.resources.FirewireInstrument.move_in
Context: PyVISA pyvisa.resources.FirewireInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](firewire-instrument.md)

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

Move a data block from the given address space and offset into local memory.

This maps to the VISA library viMoveIn\* functions.

Parameters:

- **space** (constants.AddressSpace) – Address space from which data is moved.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset, in bytes, for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Bit count to read for each element.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use a 64 bits offset regardless of platform. Defaults to False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (constants.StatusCode) – Status returned by the library call.

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised when width is invalid.

