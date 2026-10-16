# pyvisa.constants.EventType

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class EventType(enum.IntEnum):
    """The available event types for event handling."""

    #: Notification that an asynchronous operation has completed.
    io_completion = VI_EVENT_IO_COMPLETION

    #: Notification that a trigger interrupt was received from the device.
    #: For VISA, the only triggers that can be sensed are VXI hardware triggers
    #: on the assertion edge (SYNC and ON trigger protocols only).
    trig = VI_EVENT_TRIG

    #: Notification that a service request was received from the device.
    service_request = VI_EVENT_SERVICE_REQ

    #: Notification that the local controller has been sent a device clear message.
    clear = VI_EVENT_CLEAR

    #: Notification that an error condition has occurred during an operation
    #: invocation.
    exception = VI_EVENT_EXCEPTION

    #: Notification that the GPIB controller has gained or lost CIC (controller
    #: in charge) status.
    gpib_controller_in_charge = VI_EVENT_GPIB_CIC

    #: Notification that the GPIB controller has been addressed to talk.
    gpib_talk = VI_EVENT_GPIB_TALK

    #: Notification that the GPIB controller has been addressed to listen.
    gpib_listen = VI_EVENT_GPIB_LISTEN

    #: Notification that the VXI/VME SYSFAIL* line has been asserted.
    vxi_vme_sysfail = VI_EVENT_VXI_VME_SYSFAIL

    #: Notification that the VXI/VME SYSRESET* line has been asserted.
    vxi_vme_sysreset = VI_EVENT_VXI_VME_SYSRESET

    #: Notification that a VXIbus signal or VXIbus interrupt was received from
    #: the device.
    vxi_signal_interrupt = VI_EVENT_VXI_SIGP

    #: Notification that a VXIbus interrupt was received from the device.
    vxi_vme_interrupt = VI_EVENT_VXI_VME_INTR

    #: Notification that a PCI Interrupt was received from the device.
    pxi_interrupt = VI_EVENT_PXI_INTR

    #: Notification that a TCP/IP connection has been made.
    tcpip_connect = VI_EVENT_TCPIP_CONNECT

    #: Notification that a vendor-specific USB interrupt was received from the device.
    usb_interrupt = VI_EVENT_USB_INTR

    #: Value equivalent to all events. Use to switch handling mechanism for all
    #: events in one call or disabling all events.
    all_enabled = VI_ALL_ENABLED_EVENTS
```

[Source license and checked revision](../../pyvisa-source-license.md).
