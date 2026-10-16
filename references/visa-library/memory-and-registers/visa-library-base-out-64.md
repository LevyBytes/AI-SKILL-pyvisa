# pyvisa.highlevel.VisaLibraryBase.out_64
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
out_64(
    session: VISASession,
    space: AddressSpace,
    offset: int,
    data: Iterable[int],
    extended: bool = False,
) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Write a 64-bit value to the specified memory space and offset.

Corresponds to viOut64\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space into which to write.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits offset independent of the platform.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

