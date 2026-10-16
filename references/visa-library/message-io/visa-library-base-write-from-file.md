# pyvisa.highlevel.VisaLibraryBase.write_from_file
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)



```text
write_from_file(
    session: VISASession,
    filename: str,
    count: int,
) → Tuple[int, StatusCode]
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [int](https://docs.python.org/3/library/functions.html#int)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Take data from a file and write it out synchronously.

Corresponds to viWriteFromFile function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **filename** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Name of file from which data will be read.

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to be written.

Returns:

- int – Number of bytes actually transferred

- StatusCode – Return value of the library call.

