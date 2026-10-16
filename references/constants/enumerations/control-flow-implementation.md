# pyvisa.constants.ControlFlow

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class ControlFlow(enum.IntFlag):
    """Control flow for a serial resource."""

    none = VI_ASRL_FLOW_NONE
    xon_xoff = VI_ASRL_FLOW_XON_XOFF
    rts_cts = VI_ASRL_FLOW_RTS_CTS
    dtr_dsr = VI_ASRL_FLOW_DTR_DSR


# USB specific constants
```

[Source license and checked revision](../../pyvisa-source-license.md).
