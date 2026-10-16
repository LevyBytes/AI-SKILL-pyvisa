# pyvisa.highlevel.VisaLibraryBase.move_in
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
move_in(
    session: VISASession,
    space: AddressSpace,
    offset: int,
    length: int,
    width: Literal[8, 16, 32, 64] | DataWidth,
    extended: bool = False,
) → Tuple[List[int], StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [List](https://docs.python.org/3/library/typing.html#typing.List)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Moves a data block from the given address space and offset into local memory.

Corresponds to viMoveIn\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space from which to move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) - Bit width applied when reading each individual element.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (StatusCode) – Return value of the library call.

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

