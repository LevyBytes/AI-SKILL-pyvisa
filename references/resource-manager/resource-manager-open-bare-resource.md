# pyvisa.highlevel.ResourceManager.open_bare_resource
Context: PyVISA pyvisa.highlevel.ResourceManager; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../constants/constants-and-resource-manager-index.md) / [Owning VISA resource class and backend contract](resource-manager.md)

```text
open_bare_resource(
    resource_name: str,
    access_mode: AccessModes = AccessModes.no_lock,
    open_timeout: int = 0,
) → Tuple[VISASession, StatusCode]
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes)
- [int](https://docs.python.org/3/library/functions.html#int)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [VISASession, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Open the specified resource without wrapping it in a class.

Parameters:

- **resource_name** ([str](https://docs.python.org/3/library/stdtypes.html#str)) - Resource name or alias to open.

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), optional) - Access mode for the resource; defaults to constants.AccessModes.no_lock

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int), optional) - If the `access_mode` parameter asks for a lock, this absolute wait time (in milliseconds) controls how long the resource may remain locked before an error is returned; defaults to constants.VI_TMO_IMMEDIATE.

Returns:

- VISASession - Unique logical identifier reference for a session.

- StatusCode - Return value from the library call.

