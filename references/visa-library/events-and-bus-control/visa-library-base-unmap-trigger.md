# pyvisa.highlevel.VisaLibraryBase.unmap_trigger
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
unmap_trigger(
    session: VISASession,
    trigger_source: InputTriggerLine,
    trigger_destination: OutputTriggerLine,
) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Reverses an existing mapping between a trigger source line and a destination line.

Corresponds to viUnmapTrigger function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **trigger_source** (constants.InputTriggerLine) – Source line used in previous map.

- **trigger_destination** (constants.OutputTriggerLine) – Destination line used in previous map.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

