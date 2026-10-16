# pyvisa.highlevel.VisaLibraryBase.move
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
move(
    session: VISASession,
    source_space: AddressSpace,
    source_offset: int,
    source_width: DataWidth,
    destination_space: AddressSpace,
    destination_offset: int,
    destination_width: DataWidth,
    length: int,
) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Moves a block of data.

Corresponds to viMove function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **source_space** (constants.AddressSpace) – Specifies the address space of the source.

- **source_offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset of the starting address or register from which to read.

- **source_width** (constants.DataWidth) – Specifies the data width of the source.

- **destination_space** (constants.AddressSpace) – Specifies the address space of the destination.

- **destination_offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset of the starting address or register to which to write.

- **destination_width** (constants.DataWidth) – Specifies the data width of the destination.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

