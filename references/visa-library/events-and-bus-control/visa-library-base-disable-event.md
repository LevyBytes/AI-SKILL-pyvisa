# pyvisa.highlevel.VisaLibraryBase.disable_event
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
disable_event(
    session: VISASession,
    event_type: EventType,
    mechanism: EventMechanism,
) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Disable notification for an event type(s) via the specified mechanism(s).

Corresponds to viDisableEvent function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **event_type** (constants.EventType) – Event type.

- **mechanism** (constants.EventMechanism) – Event handling mechanisms to be disabled.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

