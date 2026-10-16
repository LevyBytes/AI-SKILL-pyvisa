# pyvisa.resources.GPIBInterface
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md)

```text
class pyvisa.resources.GPIBInterface(resource_manager: ResourceManager, resource_name: str)
```

Type and source details:

- [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager)
- [str](https://docs.python.org/3/library/stdtypes.html#str)

Communicates with to devices of type GPIB::INTFC

More complex resource names can be specified with the following grammar:

GPIB[board]::INTFC

Do not instantiate directly, use [`pyvisa.highlevel.ResourceManager.open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource).

