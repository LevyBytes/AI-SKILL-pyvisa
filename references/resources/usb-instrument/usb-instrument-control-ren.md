# pyvisa.resources.USBInstrument.control_ren
Context: PyVISA pyvisa.resources.USBInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](usb-instrument.md)

```text
control_ren(mode: RENLineOperation) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Controls the state of the GPIB Remote Enable (REN) interface line.

The remote/local state of the device can also be controlled optionally.

Corresponds to viGpibControlREN function of the VISA library.

Parameters:

**mode** (constants.RENLineOperation) – Sets the REN line state and, optionally, the device remote/local state.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

