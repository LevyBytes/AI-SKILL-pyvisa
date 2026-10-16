# pyvisa.resources.GPIBInterface.pass_control
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)



```text
pass_control(primary_address: int, secondary_address: int) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Instruct a GPIB device to take over as controller in charge (CIC).

This maps to the VISA library viGpibPassControl function.

Parameters:

- **primary_address** ([int](https://docs.python.org/3/library/functions.html#int)) – Primary address for the GPIB device that should receive control.

- **secondary_address** ([int](https://docs.python.org/3/library/functions.html#int)) – Secondary address for the selected GPIB device. Use Constants.NO_SEC_ADDR when that device has no secondary address.

Returns:

Status returned by the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

