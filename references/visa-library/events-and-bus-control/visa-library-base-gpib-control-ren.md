# pyvisa.highlevel.VisaLibraryBase.gpib_control_ren
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
gpib_control_ren(session: VISASession, mode: RENLineOperation) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Controls the state of the GPIB Remote Enable (REN) interface line.

Optionally the remote/local state of the device can also be set.

Corresponds to viGpibControlREN function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mode** (constants.RENLineOperation) – State for the REN line and, optionally, the device remote/local state.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

