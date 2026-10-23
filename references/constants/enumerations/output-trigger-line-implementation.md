# pyvisa.constants.OutputTriggerLine

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class OutputTriggerLine(enum.IntEnum):
    """Trigger lines to which another line can be mapped to.

    VXI, PXI devices.

    """

    #: TTL trigger lines
    ttl0 = VI_TRIG_TTL0
    ttl1 = VI_TRIG_TTL1
    ttl2 = VI_TRIG_TTL2
    ttl3 = VI_TRIG_TTL3
    ttl4 = VI_TRIG_TTL4
    ttl5 = VI_TRIG_TTL5
    ttl6 = VI_TRIG_TTL6
    ttl7 = VI_TRIG_TTL7

    # PXI specific TTL trigger lines
    ttl8 = VI_TRIG_TTL8
    ttl9 = VI_TRIG_TTL9
    ttl10 = VI_TRIG_TTL10
    ttl11 = VI_TRIG_TTL11

    #: VXI ECL trigger lines
    ecl0 = VI_TRIG_ECL0
    ecl1 = VI_TRIG_ECL1
    ecl2 = VI_TRIG_ECL2
    ecl3 = VI_TRIG_ECL3
    ecl4 = VI_TRIG_ECL4
    ecl5 = VI_TRIG_ECL5

    #: VXI STAR trigger out lines
    vxi0 = VI_TRIG_STAR_VXI0
    vxi1 = VI_TRIG_STAR_VXI1
    vxi2 = VI_TRIG_STAR_VXI2

    #: Panel OUT trigger line
    panel = VI_TRIG_PANEL_OUT

    #: All trigger lines (used only when unmapping lines)
    all = VI_TRIG_ALL
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
