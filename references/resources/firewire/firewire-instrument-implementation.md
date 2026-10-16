# pyvisa.resources.firewire.FirewireInstrument

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](firewire-module-imports-implementation.md)

```python
@RegisterBasedResource.register(constants.InterfaceType.firewire, "INSTR")
class FirewireInstrument(RegisterBasedResource):
    """Communicates with devices of type VXI::VXI logical address[::INSTR]

    More complex resource names can be specified with the following grammar:
        VXI[board]::VXI logical address[::INSTR]

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """
```

[Source license and checked revision](../../pyvisa-source-license.md).
