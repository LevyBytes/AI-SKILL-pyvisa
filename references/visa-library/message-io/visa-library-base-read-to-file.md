# pyvisa.highlevel.VisaLibraryBase.read_to_file
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
read_to_file(
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

Read data synchronously, and store the transferred data in a file.

Corresponds to viReadToFile function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **filename** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Name of file to which data will be written.

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to be read.

Returns:

- int – Number of bytes actually transferred

- StatusCode – Return value of the library call.

