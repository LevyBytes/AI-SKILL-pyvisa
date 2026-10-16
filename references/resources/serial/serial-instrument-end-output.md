# pyvisa.resources.SerialInstrument.end_output
Context: PyVISA pyvisa.resources.SerialInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](serial-instrument.md)

```text
end_output: Attribute[SerialTermination]
```

Type and source details:

- [SerialTermination](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.SerialTermination)

Write-operation termination method. The default, constants.SerialTermination.none (VI_ASRL_END_NONE), ends after all requested data transfers or an error occurs.

