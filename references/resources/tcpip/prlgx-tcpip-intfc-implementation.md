# pyvisa.resources.tcpip.PrlgxTCPIPIntfc

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](tcpip-module-imports-implementation.md)

```python
@Resource.register(constants.InterfaceType.prlgx_tcpip, "INTFC")
class PrlgxTCPIPIntfc(MessageBasedResource):
    """Communicates with to devices of type PRLGX-TCPIP::host address::port::INTFC

    More complex resource names can be specified with the following grammar:
        PRLGX-TCPIP[board]::host address::port::INTFC

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    pass
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
