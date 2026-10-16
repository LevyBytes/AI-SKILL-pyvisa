# pyvisa.resources.tcpip.VICPInstrument

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](tcpip-module-imports-implementation.md)

```python
@Resource.register(constants.InterfaceType.vicp, "INSTR")
class VICPInstrument(ControlRenMixin, MessageBasedResource):
    """Communicates with to devices of type VICP::host address[::INSTR]

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    pass
```

[Source license and checked revision](../../pyvisa-source-license.md).
