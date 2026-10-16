# pyvisa.resources.pxi.PXICommon

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](pxi-module-imports-implementation.md)

```python
class PXICommon(RegisterBasedResource):
    """Common parent class for PXI INSTR and MEMACC resources."""

    #: Number of elements by which to increment the source offset after a transfer.
    source_increment: Attribute[int] = attributes.AttrVI_ATTR_SRC_INCREMENT()

    #: Number of elements by which to increment the destination offset after a transfer.
    destination_increment: Attribute[int] = attributes.AttrVI_ATTR_DEST_INCREMENT()

    #: Should I/O accesses use DMA (True) or Programmed I/O (False).
    allow_dma: Attribute[bool] = attributes.AttrVI_ATTR_DMA_ALLOW_EN()
```

[Source license and checked revision](../../pyvisa-source-license.md).
