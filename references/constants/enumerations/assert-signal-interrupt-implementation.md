# pyvisa.constants.AssertSignalInterrupt

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class AssertSignalInterrupt(enum.IntEnum):
    """Line on which to perform an assertion or interrupt.

    Used only for VXI backplane and servant resources.

    """

    #: Use a VXI signal
    signal = VI_ASSERT_SIGNAL

    #: Use the mechanism specified in the response of Asynchronous Mode Control
    #: command. (VXI SERVANT only)
    use_assigned = VI_ASSERT_USE_ASSIGNED

    #: Send the interrupt via the specified VXI/VME IRQ line
    irq1 = VI_ASSERT_IRQ1
    irq2 = VI_ASSERT_IRQ2
    irq3 = VI_ASSERT_IRQ3
    irq4 = VI_ASSERT_IRQ4
    irq5 = VI_ASSERT_IRQ5
    irq6 = VI_ASSERT_IRQ6
    irq7 = VI_ASSERT_IRQ7
```

[Source license and checked revision](../../pyvisa-source-license.md).
