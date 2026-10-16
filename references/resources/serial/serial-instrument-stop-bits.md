# pyvisa.resources.SerialInstrument.stop_bits
Context: PyVISA pyvisa.resources.SerialInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](serial-instrument.md)

```text
stop_bits: Attribute[StopBits]
```

Type and source details:

- [StopBits](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StopBits)

Stop-bit count that marks the end of a frame. The default is constants.StopBits.one (VI_ASRL_STOP_ONE).

