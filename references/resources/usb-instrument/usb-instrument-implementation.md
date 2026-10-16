# pyvisa.resources.usb.USBInstrument

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](../usb/usb-module-imports-implementation.md)

```python
@MessageBasedResource.register(constants.InterfaceType.usb, "INSTR")
class USBInstrument(ControlRenMixin, USBCommon):
    """USB INSTR resources USB::manufacturer ID::model code::serial number

    More complex resource names can be specified with the following grammar:
        USB[board]::manufacturer ID::model code::serial number[::USB interface number][::INSTR]

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    #: Whether the device is 488.2 compliant.
    is_4882_compliant: Attribute[bool] = attributes.AttrVI_ATTR_4882_COMPLIANT()
```

[Source license and checked revision](../../pyvisa-source-license.md).
