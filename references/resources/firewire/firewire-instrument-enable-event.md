# pyvisa.resources.FirewireInstrument.enable_event
Context: PyVISA pyvisa.resources.FirewireInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](firewire-instrument.md)

```text
enable_event(
    event_type: EventType,
    mechanism: EventMechanism,
    context: None = None,
) → None
```

Type and source details:

- [None](https://docs.python.org/3/library/constants.html#None)

Enable occurrences for the selected event types and mechanisms on this resource.

Parameters:

- **event_type** (constants.EventType) – Logical identifier for the event.

- **mechanism** (constants.EventMechanism) – Event handling mechanisms to enable

- **context** (None) – Currently unused; leave it as None.

