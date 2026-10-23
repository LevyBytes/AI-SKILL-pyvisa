# pyvisa.resources.vxi.VXIInstrument

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](../vxi/vxi-module-imports-implementation.md)

```python
@Resource.register(constants.InterfaceType.vxi, "INSTR")
class VXIInstrument(VXICommon):
    """Communicates with to devices of type VXI::VXI logical address[::INSTR]

    More complex resource names can be specified with the following grammar:
        VXI[board]::VXI logical address[::INSTR]

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    #: Manufacturer name.
    manufacturer_name: Attribute[str] = attributes.AttrVI_ATTR_MANF_NAME()

    #: Manufacturer identification number of the device.
    manufacturer_id: Attribute[int] = attributes.AttrVI_ATTR_MANF_ID()

    #: Model name of the device.
    model_name: Attribute[str] = attributes.AttrVI_ATTR_MODEL_NAME()

    #: Model code for the device.
    model_code: Attribute[int] = attributes.AttrVI_ATTR_MODEL_CODE()

    #: Whether the device is 488.2 compliant.
    is_4882_compliant: Attribute[bool] = attributes.AttrVI_ATTR_4882_COMPLIANT()

    #: Should END be asserted during the transfer of the last byte of the buffer.
    send_end: Attribute[bool] = attributes.AttrVI_ATTR_SEND_END_EN()

    #: IO protocol to use. See the attribute definition for more details.
    io_protocol: Attribute[constants.IOProtocol] = attributes.AttrVI_ATTR_IO_PROT()
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
