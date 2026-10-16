# pyvisa.constants.EventAttribute

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class EventAttribute(enum.IntEnum):
    """The possible attributes of VISA events."""

    event_type = VI_ATTR_EVENT_TYPE
    status = VI_ATTR_STATUS
    operation_name = VI_ATTR_OPER_NAME
    job_id = VI_ATTR_JOB_ID
    return_count = VI_ATTR_RET_COUNT
    buffer = VI_ATTR_BUFFER
    received_trigger_id = VI_ATTR_RECV_TRIG_ID
    gpib_received_cic_state = VI_ATTR_GPIB_RECV_CIC_STATE
    received_tcpip_connect = VI_ATTR_RECV_TCPIP_ADDR
    usb_received_interrupt_size = VI_ATTR_USB_RECV_INTR_SIZE
    usb_received_interrupt_data = VI_ATTR_USB_RECV_INTR_DATA
    signal_register_status_id = VI_ATTR_SIGP_STATUS_ID
    interrupt_status_id = VI_ATTR_INTR_STATUS_ID
    received_interrupt_level = VI_ATTR_RECV_INTR_LEVEL
    pxi_received_interrupt_sequence = VI_ATTR_PXI_RECV_INTR_SEQ
    pxi_received_interrupt_data = VI_ATTR_PXI_RECV_INTR_DATA
```

[Source license and checked revision](../../pyvisa-source-license.md).
