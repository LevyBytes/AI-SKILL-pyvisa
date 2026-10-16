# pyvisa.resources.serial.PrlgxASRLIntfc

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](serial-module-imports-implementation.md)

```python
@MessageBasedResource.register(constants.InterfaceType.prlgx_asrl, "INTFC")
class PrlgxASRLIntfc(SerialInstrument):
    """Communicates with devices of type PRLGX-ASRL::serial device::INTFC

    More complex resource names can be specified with the following grammar:
        PRLGX-ASRL[board]::serial device::INTFC

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    pass
```

[Source license and checked revision](../../pyvisa-source-license.md).
