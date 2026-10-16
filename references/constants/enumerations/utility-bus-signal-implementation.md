# pyvisa.constants.UtilityBusSignal

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class UtilityBusSignal(enum.IntEnum):
    """Operation on the utility line of a VXI backplane or servant."""

    #: Assert the SYSRESET ie perform a HARD RESET on the whole VXI bus.
    sysrest = VI_UTIL_ASSERT_SYSRESET

    #: Assert the SYSFAIL line.
    sysfail_assert = VI_UTIL_ASSERT_SYSFAIL

    #: Deassert the SYSFAIL line.
    sysfail_deassert = VI_UTIL_DEASSERT_SYSFAIL
```

[Source license and checked revision](../../pyvisa-source-license.md).
