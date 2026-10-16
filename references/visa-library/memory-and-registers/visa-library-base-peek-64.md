# pyvisa.highlevel.VisaLibraryBase.peek_64
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
peek_64(session: VISASession, address: VISAMemoryAddress) → Tuple[int, StatusCode]
```

Type and source details:

- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Read an 64-bit value from the specified address.

Corresponds to viPeek64 function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

Returns:

- int – Data read from bus

- StatusCode – Return value of the library call.

