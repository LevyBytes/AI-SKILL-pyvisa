# pyvisa.highlevel.VisaLibraryBase.in_8
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Source context](../visa-library-base-low-level-api-index.md) / [Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)


```text
in_8(
    session: VISASession,
    space: AddressSpace,
    offset: int,
    extended: bool = False,
) → Tuple[int, StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Reads an 8-bit value from the selected memory space and offset.

Corresponds to viIn8\* function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Specifies the address space.

-
**offset** ([_int_](https://docs.python.org/3/library/functions.html#int)) - Byte offset for the address or register used by the read.

-
**extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits for offsets regardless of platform; False by default.

Returns:

- int – Data read from memory

- StatusCode – Return value of the library call.

