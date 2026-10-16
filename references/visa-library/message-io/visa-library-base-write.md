# pyvisa.highlevel.VisaLibraryBase.write
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
write(session: VISASession, data: bytes) → Tuple[int, StatusCode]
```

Type and source details:

- [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Write data to device or interface synchronously.

Corresponds to viWrite function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – Data to be written.

Returns:

- int – Number of bytes actually transferred

- StatusCode – Return value of the library call.

