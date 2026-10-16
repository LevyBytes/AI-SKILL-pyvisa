# pyvisa.highlevel.VisaLibraryBase.vxi_command_query
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
vxi_command_query(
    session: VISASession,
    mode: VXICommands,
    command: int,
) → Tuple[int, StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Sends a miscellaneous command or query to the device and/or retrieves an earlier query response.

Corresponds to viVxiCommandQuery function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mode** (constants.VXICommands) – Specifies whether to issue a command, retrieve a response, or both.

- **command** ([int](https://docs.python.org/3/library/functions.html#int)) – The miscellaneous command to send.

Returns:

- int – The response retrieved from the device

- StatusCode – Return value of the library call.

