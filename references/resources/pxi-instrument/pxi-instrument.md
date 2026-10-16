# pyvisa.resources.PXIInstrument
Context: PyVISA pyvisa.resources.PXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md)

```text
class pyvisa.resources.PXIInstrument(resource_manager: ResourceManager, resource_name: str)
```

Type and source details:

- [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager)
- [str](https://docs.python.org/3/library/stdtypes.html#str)

Communicates with to devices of type PXI::&lt;device&gt;[::INSTR]

More complex resource names can be specified with the following grammar:

PXI[bus]::device[::function][::INSTR]

or:

PXI[interface]::bus-device[.function][::INSTR]

or:

PXI[interface]::CHASSISchassis number::SLOTslot number[::FUNCfunction][::INSTR]

Do not instantiate directly, use [`pyvisa.highlevel.ResourceManager.open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource).

