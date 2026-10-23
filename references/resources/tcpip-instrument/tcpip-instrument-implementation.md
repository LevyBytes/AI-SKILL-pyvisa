# pyvisa.resources.tcpip.TCPIPInstrument

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](../tcpip/tcpip-module-imports-implementation.md)

```python
@Resource.register(constants.InterfaceType.tcpip, "INSTR")
class TCPIPInstrument(ControlRenMixin, MessageBasedResource):
    """Communicates with to devices of type TCPIP::host address[::INSTR]

    More complex resource names can be specified with the following grammar:
        TCPIP[board]::host address[::LAN device name][::INSTR]

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    pass
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
