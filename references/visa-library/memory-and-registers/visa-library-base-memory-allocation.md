# pyvisa.highlevel.VisaLibraryBase.memory_allocation
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
memory_allocation(
    session: VISASession,
    size: int,
    extended: bool = False,
) → Tuple[int, StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Allocate memory from a resource’s memory region.

Corresponds to viMemAlloc\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **size** ([int](https://docs.python.org/3/library/functions.html#int)) – Specifies the size of the allocation.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits offset independent of the platform.

Returns:

- int – offset of the allocated memory

- StatusCode – Return value of the library call.

