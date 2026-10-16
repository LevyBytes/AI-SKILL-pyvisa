# pyvisa.highlevel.VisaLibraryBase.poke
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
poke(
    session: VISASession,
    address: VISAMemoryAddress,
    width: Literal[8, 16, 32, 64] | DataWidth,
    data: int,
) → StatusCode
```

Type and source details:

- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Writes a value of 8, 16, 32, or 64-bit width from the specified address.

Corresponds to viPoke\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Number of bits that should be read.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to the bus

Returns:

**status_code** – Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

