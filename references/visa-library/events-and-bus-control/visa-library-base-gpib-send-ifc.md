# pyvisa.highlevel.VisaLibraryBase.gpib_send_ifc
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
gpib_send_ifc(session: VISASession) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Pulse the interface clear line (IFC) for at least 100 microseconds.

Corresponds to viGpibSendIFC function of the VISA library.

Parameters:

**session** (VISASession) – Unique logical identifier to a session.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

