# pyvisa.highlevel.VisaLibraryBase.read_stb
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
read_stb(session: VISASession) → Tuple[int, StatusCode]
```

Type and source details:

- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Reads a status byte of the service request.

Corresponds to viReadSTB function of the VISA library.

Parameters:

**session** (VISASession) – Unique logical identifier to a session.

Returns:

- int – Service request status byte

- StatusCode – Return value of the library call.

