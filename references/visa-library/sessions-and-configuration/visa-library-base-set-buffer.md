# pyvisa.highlevel.VisaLibraryBase.set_buffer
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
set_buffer(
    session: VISASession,
    mask: BufferType,
    size: int,
) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Sets the size of the formatted I/O buffer(s), low-level I/O communication buffer(s), or both.

Corresponds to viSetBuf function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mask** (constants.BufferType) – Specifies the type of buffer.

- **size** ([int](https://docs.python.org/3/library/functions.html#int)) – The size to be set for the specified buffer(s).

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

