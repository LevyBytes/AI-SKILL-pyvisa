# pyvisa.highlevel.ResourceManager.list_resources_info
Context: PyVISA pyvisa.highlevel.ResourceManager; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../constants/constants-and-resource-manager-index.md) / [Owning VISA resource class and backend contract](resource-manager.md)

```text
list_resources_info(query: str = '?*::INSTR') → Dict[str, ResourceInfo]
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [Dict](https://docs.python.org/3/library/typing.html#typing.Dict)

Get extended details for all connected devices that match query.

For the VISA Resource Regular Expression syntax used by query, see list_resources().

Returns:

Mapping from resource name to ResourceInfo

Return type:

Dict[[str](https://docs.python.org/3/library/stdtypes.html#str), ResourceInfo]

