# pyvisa.highlevel.VisaLibraryBase.status_description
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
status_description(session: VISASession, status: StatusCode) → Tuple[str, StatusCode]
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [str](https://docs.python.org/3/library/stdtypes.html#str)

Returns a user-readable description for the status code supplied to the operation.

Corresponds to viStatusDesc function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **status** ([StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)) – Status code to interpret.

Returns:

- str – User-readable string interpretation of the status code.

- StatusCode – Return value of the library call.

