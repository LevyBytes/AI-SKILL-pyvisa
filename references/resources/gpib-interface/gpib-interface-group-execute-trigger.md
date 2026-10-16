# pyvisa.resources.GPIBInterface.group_execute_trigger
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
group_execute_trigger(*resources: GPIBInstrument) → Tuple[int, StatusCode]
```

Type and source details:

- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Parameters:

**resources** (GPIBInstrument) – GPIB resources to which to send the group trigger.

Returns:

- int – Number of bytes written as part of sending the GPIB commands.

- constants.StatusCode – Return value of the library call.

