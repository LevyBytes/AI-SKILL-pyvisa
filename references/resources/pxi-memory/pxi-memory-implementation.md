# pyvisa.resources.pxi.PXIMemory

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](../pxi/pxi-module-imports-implementation.md)

```python
@Resource.register(constants.InterfaceType.pxi, "MEMACC")
class PXIMemory(PXICommon):
    """Communicates with to devices of type PXI[interface]::MEMACC

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """
```

[Source license and checked revision](../../pyvisa-source-license.md).
