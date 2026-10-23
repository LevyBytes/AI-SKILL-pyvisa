# pyvisa.constants.ByteOrder

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class ByteOrder(enum.IntEnum):
    """Byte order in register data transfer."""

    big_endian = VI_BIG_ENDIAN
    little_endian = VI_LITTLE_ENDIAN
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
