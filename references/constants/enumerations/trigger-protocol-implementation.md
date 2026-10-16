# pyvisa.constants.TriggerProtocol

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class TriggerProtocol(enum.IntEnum):
    """Trigger protocol used when assering a resource trigger."""

    # FIXME The VISA standard is not very detailed on those
    #: Default protocol.
    #: This is the only valid protocol for software trigger on ASRL, GPIB, USB
    #: and VXI resources
    default = VI_TRIG_PROT_DEFAULT

    #:
    on = VI_TRIG_PROT_ON

    #:
    off = VI_TRIG_PROT_OFF

    #: For VXI devices equivalent to default
    sync = VI_TRIG_PROT_SYNC

    #: On PXI resources used to reserve a line for triggering
    reserve = VI_TRIG_PROT_RESERVE

    #: On PXI resources used to unreserve a line for triggering
    unreserve = VI_TRIG_PROT_UNRESERVE
```

[Source license and checked revision](../../pyvisa-source-license.md).
