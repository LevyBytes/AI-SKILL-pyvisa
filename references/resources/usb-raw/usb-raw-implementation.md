# pyvisa.resources.usb.USBRaw

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](../usb/usb-module-imports-implementation.md)

```python
@MessageBasedResource.register(constants.InterfaceType.usb, "RAW")
class USBRaw(USBCommon):
    """USB RAW resources: USB::manufacturer ID::model code::serial number::RAW

    More complex resource names can be specified with the following grammar:
        USB[board]::manufacturer ID::model code::serial number[::USB interface number]::RAW

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """
```

[Source license and checked revision](../../pyvisa-source-license.md).
