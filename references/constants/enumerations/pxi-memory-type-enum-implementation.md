# pyvisa.constants.PXIMemory

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class PXIMemory(enum.IntEnum):
    """Memory type used in a PXI BAR."""

    none = VI_PXI_ADDR_NONE
    memory = VI_PXI_ADDR_MEM
    io = VI_PXI_ADDR_IO
    cfg = VI_PXI_ADDR_CFG
```

[Source license and checked revision](../../pyvisa-source-license.md).
