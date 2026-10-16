# pyvisa.highlevel.VisaLibraryBase.read_asynchronously
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
read_asynchronously(session: VISASession, count: int) → Tuple[SupportsBytes, VISAJobID, StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [SupportsBytes](https://docs.python.org/3/library/typing.html#typing.SupportsBytes)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Reads data from device or interface asynchronously.

Corresponds to viReadAsync function of the VISA library. Because the asynchronous operation may finish before the function call returns, implementations should make sure get_buffer_from_id can provide the proper buffer before this method returns.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to be read.

Returns:

- SupportsBytes – Buffer that will be filled during the asynchronous operation.

- VISAJobID – Id of the asynchronous job

- StatusCode – Return value of the library call.

