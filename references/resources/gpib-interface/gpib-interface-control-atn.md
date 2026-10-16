# pyvisa.resources.GPIBInterface.control_atn
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
control_atn(mode: ATNLineOperation) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Sets the ATN line state and the local active controller state.

Corresponds to viGpibControlATN function of the VISA library.

Parameters:

**mode** (constants.ATNLineOperation) –

Specifies the state of the ATN line and optionally the local active

controller state.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

