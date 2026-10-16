# pyvisa.resources.SerialInstrument.end_input
Context: PyVISA pyvisa.resources.SerialInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](serial-instrument.md)

```text
end_input: Attribute[SerialTermination]
```

Type and source details:

- [SerialTermination](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.SerialTermination)

Method used to terminate read operations. The default value is constants.SerialTermination.termination_char (VI_ASRL_END_TERMCHAR).

