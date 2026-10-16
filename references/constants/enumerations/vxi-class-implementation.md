# pyvisa.constants.VXIClass

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class VXIClass(enum.IntEnum):
    """VXI-defined device class."""

    memory = VI_VXI_CLASS_MEMORY
    extended = VI_VXI_CLASS_EXTENDED
    message = VI_VXI_CLASS_MESSAGE
    register = VI_VXI_CLASS_REGISTER
    other = VI_VXI_CLASS_OTHER
```

[Source license and checked revision](../../pyvisa-source-license.md).
