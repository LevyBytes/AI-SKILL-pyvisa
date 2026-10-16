# pyvisa.highlevel.VisaLibraryBase.memory_free
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
memory_free(
    session: VISASession,
    offset: int,
    extended: bool = False,
) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Frees memory previously allocated using the memory_allocation() operation.

Corresponds to viMemFree\* function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset of the memory to free.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits offset independent of the platform.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

