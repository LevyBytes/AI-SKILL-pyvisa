# pyvisa.highlevel.VisaLibraryBase.enable_event
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
enable_event(
    session: VISASession,
    event_type: EventType,
    mechanism: EventMechanism,
    context: None = None,
) → StatusCode
```

Type and source details:

- [None](https://docs.python.org/3/library/constants.html#None)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Enable event occurrences for specified event types and mechanisms in a session.

Corresponds to viEnableEvent function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **event_type** (constants.EventType) – Logical event identifier.

- **mechanism** (constants.EventMechanism) – Specifies event handling mechanisms to be enabled.

- **context** (None, optional) – Unused parameter…

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

