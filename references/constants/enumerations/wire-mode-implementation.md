# pyvisa.constants.WireMode

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class WireMode(enum.IntEnum):
    """Valid modes for National Instruments hardware supporting it."""

    #: 4-wire mode.
    rs485_4 = VI_ASRL_WIRE_485_4

    #: 2-wire DTR mode controlled with echo.
    rs485_2_dtr_echo = VI_ASRL_WIRE_485_2_DTR_ECHO

    #: 2-wire DTR mode controlled without echo
    rs485_2_dtr_ctrl = VI_ASRL_WIRE_485_2_DTR_CTRL

    #: 2-wire auto mode controlled with TXRDY
    rs485_2_auto = VI_ASRL_WIRE_485_2_AUTO

    #: Use DTE mode
    rs232_dte = VI_ASRL_WIRE_232_DTE

    #: Use DCE mode
    rs232_dce = VI_ASRL_WIRE_232_DCE

    #: Auto detect the mode to use
    rs232_auto = VI_ASRL_WIRE_232_AUTO

    #: Unknown mode
    unknown = VI_STATE_UNKNOWN
```

[Source license and checked revision](../../pyvisa-source-license.md).
