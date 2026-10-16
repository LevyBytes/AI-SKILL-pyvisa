# pyvisa.highlevel.VisaLibraryBase.move_out
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
move_out(
    session: VISASession,
    space: AddressSpace,
    offset: int,
    length: int,
    data: Iterable[int],
    width: Literal[8, 16, 32, 64] | DataWidth,
    extended: bool = False,
) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Moves a data block from local memory to the specified address space and offset.

Corresponds to viMoveOut\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space into which move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

-
**length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **data** (Iterable[[int](https://docs.python.org/3/library/functions.html#int)]) – Data to write to bus.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Number of bits used for each element.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

