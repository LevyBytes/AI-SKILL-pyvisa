# pyvisa.highlevel.VisaLibraryBase.read_memory
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
read_memory(
    session: VISASession,
    space: AddressSpace,
    offset: int,
    width: Literal[8, 16, 32, 64] | DataWidth,
    extended: bool = False,
) → Tuple[int, StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Read a value from the specified memory space and offset.

Corresponds to viIn\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Specifies the address space from which to read.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Number of bits to read (8, 16, 32 or 64).

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits offset independent of the platform.

Returns:

- **data** (int) – Data read from memory

- **status_code** (StatusCode) – Return value of the library call.

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

