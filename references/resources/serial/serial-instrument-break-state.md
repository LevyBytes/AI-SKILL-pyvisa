# pyvisa.resources.SerialInstrument.break_state
Context: PyVISA pyvisa.resources.SerialInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](serial-instrument.md)

```text
break_state: Attribute[LineState]
```

Type and source details:

- [LineState](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.LineState)

Manually sets the break signal assertion state. Defaults to constants.LineState.unasserted (VI_STATE_UNASSERTED).

