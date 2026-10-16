# pyvisa.resources.GPIBInterface.send_ifc
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
send_ifc() → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Pulse the interface clear line (IFC) for at least 100 microseconds.

This maps to the VISA library viGpibSendIFC function.

