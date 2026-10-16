# pyvisa.resources.SerialInstrument.flow_control
Context: PyVISA pyvisa.resources.SerialInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](serial-instrument.md)

```text
flow_control: Attribute[ControlFlow]
```

Flow-control type used by the transfer mechanism. The default is constants.ControlFlow.none (VI_ASRL_FLOW_NONE).

