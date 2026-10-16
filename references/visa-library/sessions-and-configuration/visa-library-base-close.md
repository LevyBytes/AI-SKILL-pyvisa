# pyvisa.highlevel.VisaLibraryBase.close
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
close(session: VISASession | VISAEventContext | VISARMSession) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Closes the specified session, event, or find list.

Corresponds to viClose function of the VISA library.

Parameters:

**session** (Union[VISASession, VISAEventContext, VISARMSession]) – Unique logical identifier for a session, event, or resource manager.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

