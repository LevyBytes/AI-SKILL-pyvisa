# pyvisa.resources.pxi.PXIInstrument

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](../pxi/pxi-module-imports-implementation.md)

```python
@Resource.register(constants.InterfaceType.pxi, "INSTR")
class PXIInstrument(PXICommon):
    """Communicates with to devices of type PXI::<device>[::INSTR]

    More complex resource names can be specified with the following grammar:
        PXI[bus]::device[::function][::INSTR]
    or:
        PXI[interface]::bus-device[.function][::INSTR]
    or:
        PXI[interface]::CHASSISchassis number::SLOTslot number[::FUNCfunction][::INSTR]

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
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
