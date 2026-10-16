# pyvisa.highlevel.VisaLibraryBase.peek
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
peek(
    session: VISASession,
    address: VISAMemoryAddress,
    width: Literal[8, 16, 32, 64] | DataWidth,
) → Tuple[int, StatusCode]
```

Type and source details:

- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Reads a value of 8, 16, 32, or 64-bit width from the specified address.

Corresponds to viPeek\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Number of bits that should be read.

Returns:

- **data** (int) – Data read from bus

- **status_code** (StatusCode) – Return value of the library call.

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

