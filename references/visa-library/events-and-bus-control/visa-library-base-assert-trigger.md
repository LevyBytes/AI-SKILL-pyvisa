# pyvisa.highlevel.VisaLibraryBase.assert_trigger
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
assert_trigger(session: VISASession, protocol: TriggerProtocol) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Assert software or hardware trigger.

Corresponds to viAssertTrigger function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **protocol** (constants.TriggerProtocol) – Trigger protocol to use during assertion.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

