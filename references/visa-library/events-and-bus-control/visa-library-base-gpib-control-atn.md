# pyvisa.highlevel.VisaLibraryBase.gpib_control_atn
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
gpib_control_atn(session: VISASession, mode: ATNLineOperation) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Specifies the ATN line state together with the local active-controller state.

Corresponds to viGpibControlATN function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mode** (constants.ATNLineOperation) – State for the ATN line and, optionally, the local active-controller state.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

