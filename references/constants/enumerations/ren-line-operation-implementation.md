# pyvisa.constants.RENLineOperation

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class RENLineOperation(enum.IntEnum):
    """Operation that can be performed on the REN line.

    Some operations apply to GPIB INSTR, GPIB INTFC, USB INSTR,
    TCPIP INSTR, please see the VISA reference for more details.

    """

    #: Send the Go To Local command (GTL) to this device.
    address_gtl = VI_GPIB_REN_ADDRESS_GTL

    #: Assert REN line.
    asrt = VI_GPIB_REN_ASSERT

    #: Assert REN line and address this device.
    asrt_address = VI_GPIB_REN_ASSERT_ADDRESS

    #: Address this device and send it LLO, putting it in RWLS
    asrt_address_llo = VI_GPIB_REN_ASSERT_ADDRESS_LLO

    #: Send LLO to any devices that are addressed to listen.
    asrt_llo = VI_GPIB_REN_ASSERT_LLO

    #: Deassert REN line.
    deassert = VI_GPIB_REN_DEASSERT

    #: Send the Go To Local command (GTL) to this device and deassert REN line.
    deassert_gtl = VI_GPIB_REN_DEASSERT_GTL
```

[Source license and checked revision](../../pyvisa-source-license.md).
