# pyvisa.resources.vxi.VXICommon

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](vxi-module-imports-implementation.md)

```python
class VXICommon(RegisterBasedResource):
    """Common parent class for VXI INSTR and MEMACC resources."""

    #: Number of elements by which to increment the source offset after a transfer.
    source_increment: Attribute[int] = attributes.AttrVI_ATTR_SRC_INCREMENT()

    #: Number of elements by which to increment the destination offset after a transfer.
    destination_increment: Attribute[int] = attributes.AttrVI_ATTR_DEST_INCREMENT()

    #: Should I/O accesses use DMA (True) or Programmed I/O (False).
    allow_dma: Attribute[bool] = attributes.AttrVI_ATTR_DMA_ALLOW_EN()
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
