# pyvisa.highlevel.VisaLibraryBase.write_memory
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
write_memory(
    session: VISASession,
    space: AddressSpace,
    offset: int,
    data: int,
    width: Literal[8, 16, 32, 64] | DataWidth,
    extended: bool = False,
) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Write a value to the specified memory space and offset.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Specifies the address space.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Number of bits that should be read.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.
