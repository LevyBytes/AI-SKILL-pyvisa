# pyvisa.constants.InterfaceType

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class InterfaceType(enum.IntEnum):
    """The hardware interface."""

    # Used for unknown interface type strings.
    unknown = -1

    #: GPIB Interface.
    gpib = VI_INTF_GPIB

    #: VXI (VME eXtensions for Instrumentation), VME, MXI (Multisystem eXtension Interface).
    vxi = VI_INTF_VXI

    #: GPIB VXI (VME eXtensions for Instrumentation).
    gpib_vxi = VI_INTF_GPIB_VXI

    #: Serial devices connected to either an RS-232 or RS-485 controller.
    asrl = VI_INTF_ASRL

    #: PXI device.
    pxi = VI_INTF_PXI

    #: TCPIP device.
    tcpip = VI_INTF_TCPIP

    #: Universal Serial Bus (USB) hardware bus.
    usb = VI_INTF_USB

    #: Rio device.
    rio = VI_INTF_RIO

    #: Firewire device.
    firewire = VI_INTF_FIREWIRE

    #: Rohde and Schwarz Device via Passport
    rsnrp = 33024

    #: Lecroy VICP via passport
    vicp = 36000  # FIXME

    #: prologix usb
    prlgx_asrl = 34567  # an arbitrarily chosen value

    #: prologix tcpip
    prlgx_tcpip = 76543  # an arbitrarily chosen value
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
