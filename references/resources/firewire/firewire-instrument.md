# pyvisa.resources.FirewireInstrument
Context: PyVISA pyvisa.resources.FirewireInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md)

```text
class pyvisa.resources.FirewireInstrument(resource_manager: ResourceManager, resource_name: str)
```

Type and source details:

- [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager)
- [str](https://docs.python.org/3/library/stdtypes.html#str)

Communicates with devices using resource names of type VXI::VXI logical address[::INSTR].

More complex resource names may use this grammar:

VXI[board]::VXI logical address[::INSTR]

Do not instantiate this class directly; use [`pyvisa.highlevel.ResourceManager.open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource).

