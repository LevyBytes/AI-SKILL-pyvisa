# pyvisa.resources.PXIInstrument.disable_event
Context: PyVISA pyvisa.resources.PXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-instrument.md)

```text
disable_event(event_type: EventType, mechanism: EventMechanism) → None
```

Type and source details:

- [None](https://docs.python.org/3/library/constants.html#None)

Disable notification for an event type(s) via the specified mechanism(s).

Parameters:

- **event_type** (constants.EventType) – Logical event identifier.

- **mechanism** (constants.EventMechanism) – Specifies event handling mechanisms to be disabled.

