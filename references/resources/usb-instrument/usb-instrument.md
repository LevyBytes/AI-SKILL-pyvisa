# pyvisa.resources.USBInstrument
Context: PyVISA pyvisa.resources.USBInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md)

```text
class pyvisa.resources.USBInstrument(resource_manager: ResourceManager, resource_name: str)
```

Type and source details:

- [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager)
- [str](https://docs.python.org/3/library/stdtypes.html#str)

USB INSTR resources USB::manufacturer ID::model code::serial number

More complex resource names can be specified with the following grammar:

USB[board]::manufacturer ID::model code::serial number[::USB interface number][::INSTR]

Do not instantiate directly, use [`pyvisa.highlevel.ResourceManager.open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource).

