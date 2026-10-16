# pyvisa.resources.FirewireInstrument.discard_events
Context: PyVISA pyvisa.resources.FirewireInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](firewire-instrument.md)

```text
discard_events(event_type: EventType, mechanism: EventMechanism) → None
```

Type and source details:

- [None](https://docs.python.org/3/library/constants.html#None)

Discard queued occurrences for an event type and mechanism on this resource.

Parameters:

- **event_type** (constants.EventType) – Logical identifier for the event.

- **mechanism** (constants.EventMechanism) – Event handling mechanisms to disable.

