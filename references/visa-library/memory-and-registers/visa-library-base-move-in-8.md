# pyvisa.highlevel.VisaLibraryBase.move_in_8
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
move_in_8(
    session: VISASession,
    space: AddressSpace,
    offset: int,
    length: int,
    extended: bool = False,
) → Tuple[List[int], StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [List](https://docs.python.org/3/library/typing.html#typing.List)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Moves an 8-bit block of data to local memory.

Corresponds to viMoveIn8\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space from which to move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (StatusCode) – Return value of the library call.

