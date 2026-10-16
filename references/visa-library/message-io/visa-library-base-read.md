# pyvisa.highlevel.VisaLibraryBase.read
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
read(session: VISASession, count: int) → Tuple[bytes, StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Reads data from device or interface synchronously.

Corresponds to viRead function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to be read.

Returns:

- bytes – Date read

- StatusCode – Return value of the library call.

