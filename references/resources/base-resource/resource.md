# pyvisa.resources.Resource
Context: PyVISA pyvisa.resources.Resource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md)

```text
class pyvisa.resources.Resource(resource_manager: ResourceManager, resource_name: str)
```

Type and source details:

- [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager)
- [str](https://docs.python.org/3/library/stdtypes.html#str)

Base class for resources.

Do not instantiate directly, use [`pyvisa.highlevel.ResourceManager.open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource).

