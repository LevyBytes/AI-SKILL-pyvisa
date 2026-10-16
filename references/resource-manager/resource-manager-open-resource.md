# pyvisa.highlevel.ResourceManager.open_resource
Context: PyVISA pyvisa.highlevel.ResourceManager; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../constants/constants-and-resource-manager-index.md) / [Owning VISA resource class and backend contract](resource-manager.md)

```text
open_resource(
    resource_name: str,
    access_mode: AccessModes = AccessModes.no_lock,
    open_timeout: int = 0,
    resource_pyclass: Type[Resource] | None = None,
    **kwargs: Any,
) → Resource
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes)
- [int](https://docs.python.org/3/library/functions.html#int)
- [Type](https://docs.python.org/3/library/typing.html#typing.Type)
- [Resource](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource)
- [None](https://docs.python.org/3/library/constants.html#None)
- [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Return an instrument matching the resource name.

Parameters:

- **resource_name** ([str](https://docs.python.org/3/library/stdtypes.html#str)) - Resource name or alias to open.

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), optional) - Access mode for the resource; defaults to constants.AccessModes.no_lock

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int), optional) - If the `access_mode` parameter asks for a lock, this absolute wait time (in milliseconds) controls how long the resource may remain locked before an error is returned; defaults to constants.VI_TMO_IMMEDIATE.

- **resource_pyclass** (Optional[Type[[Resource](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource)]], optional) - Resource Python class used to instantiate the Resource. Defaults to None, which selects based on the resource name.

- **kwargs** (Any) - Keyword arguments used to modify instrument attributes after construction.

Returns:

Subclass of Resource that matches the resource.

Return type:

[Resource](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource)

