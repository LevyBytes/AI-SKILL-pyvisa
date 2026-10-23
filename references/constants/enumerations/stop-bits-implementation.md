# pyvisa.constants.StopBits

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class StopBits(enum.IntEnum):
    """Number of stop bits marking the end of a frame on a serial resource.

    Used only for ASRL resources.

    """

    one = VI_ASRL_STOP_ONE
    one_and_a_half = VI_ASRL_STOP_ONE5
    two = VI_ASRL_STOP_TWO
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
