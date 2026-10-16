# pyvisa.constants.Timeouts

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class Timeouts(enum.IntEnum):
    """Special timeout values."""

    #: Minimal timeout value
    immediate = VI_TMO_IMMEDIATE

    #: Infinite timeout
    infinite = VI_TMO_INFINITE
```

[Source license and checked revision](../../pyvisa-source-license.md).
