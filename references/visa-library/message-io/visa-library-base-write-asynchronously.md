# pyvisa.highlevel.VisaLibraryBase.write_asynchronously
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
write_asynchronously(session: VISASession, data: bytes) → Tuple[VISAJobID, StatusCode]
```

Type and source details:

- [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [VISAJobID, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Write data to device or interface asynchronously.

Corresponds to viWriteAsync function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – Data to be written.

Returns:

- VISAJobID – Job ID of this asynchronous write operation

- StatusCode – Return value of the library call.
