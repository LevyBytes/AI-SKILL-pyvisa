# pyvisa.highlevel.ResourceManager.resource_info
Context: PyVISA pyvisa.highlevel.ResourceManager; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../constants/constants-and-resource-manager-index.md) / [Owning VISA resource class and backend contract](resource-manager.md)

```text
resource_info(resource_name: str, extended: bool = True) → ResourceInfo
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [bool](https://docs.python.org/3/library/functions.html#bool)

Get (extended) information for a specific resource.

Parameters:

- **resource_name** ([str](https://docs.python.org/3/library/stdtypes.html#str)) - Unique symbolic name of a resource.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) - Also retrieve extended information (ie. resource_class, resource_name, alias)

