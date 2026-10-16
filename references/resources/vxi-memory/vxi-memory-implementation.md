# pyvisa.resources.vxi.VXIMemory

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](../vxi/vxi-module-imports-implementation.md)

```python
@Resource.register(constants.InterfaceType.vxi, "MEMACC")
class VXIMemory(VXICommon):
    """Communicates with to devices of type VXI[board]::MEMACC

    More complex resource names can be specified with the following grammar:
        VXI[board]::MEMACC

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """
```

[Source license and checked revision](../../pyvisa-source-license.md).
