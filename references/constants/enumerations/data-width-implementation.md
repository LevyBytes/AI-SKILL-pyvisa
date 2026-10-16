# pyvisa.constants.DataWidth

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class DataWidth(enum.IntEnum):
    """Word width used when transferring data to/from register based resources."""

    #: Transfer data using 1 byte word
    bit_8 = VI_WIDTH_8

    #: Transfer data using 2 byte word
    bit_16 = VI_WIDTH_16

    #: Transfer data using 4 byte word
    bit_32 = VI_WIDTH_32

    #: Transfer data using 8 byte word
    bit_64 = VI_WIDTH_64
```

[Source license and checked revision](../../pyvisa-source-license.md).
