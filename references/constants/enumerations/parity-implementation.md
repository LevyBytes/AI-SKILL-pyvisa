# pyvisa.constants.Parity

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class Parity(enum.IntEnum):
    """Parity setting applied to every frame transmitted and received on a serial session.

    Used only for ASRL resources.

    """

    none = VI_ASRL_PAR_NONE
    odd = VI_ASRL_PAR_ODD
    even = VI_ASRL_PAR_EVEN
    mark = VI_ASRL_PAR_MARK
    space = VI_ASRL_PAR_SPACE
```

[Source license and checked revision](../../pyvisa-source-license.md).
