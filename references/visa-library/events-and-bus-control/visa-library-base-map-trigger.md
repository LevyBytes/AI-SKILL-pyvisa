# pyvisa.highlevel.VisaLibraryBase.map_trigger
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
map_trigger(
    session: VISASession,
    trigger_source: InputTriggerLine,
    trigger_destination: OutputTriggerLine,
    mode: None = None,
) → StatusCode
```

Type and source details:

- [None](https://docs.python.org/3/library/constants.html#None)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Map the specified trigger source line to the specified destination line.

Corresponds to viMapTrigger function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **trigger_source** (constants.InputTriggerLine) – Source line from which to map.

- **trigger_destination** (constants.OutputTriggerLine) – Destination line to which to map.

- **mode** (None, optional) – Always None for this version of the VISA specification.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

