# pyvisa.constants.TriggerEventID

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class TriggerEventID(enum.IntEnum):
    """Identifier of the triggering mechanism on which a trigger event was received."""

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

    #: FIXME No definition in the VISA standards
    instr = VI_TRIG_STAR_INSTR
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
