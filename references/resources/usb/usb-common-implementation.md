# pyvisa.resources.usb.USBCommon

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](usb-module-imports-implementation.md)

```python
class USBCommon(MessageBasedResource):
    """Common class for USB resources."""

    #: USB interface number used by the given session.
    interface_number: Attribute[int] = attributes.AttrVI_ATTR_USB_INTFC_NUM()

    #: USB serial number of this device.
    serial_number: Attribute[str] = attributes.AttrVI_ATTR_USB_SERIAL_NUM()

    #: USB protocol used by this USB interface.
    usb_protocol: Attribute[int] = attributes.AttrVI_ATTR_USB_PROTOCOL()

    #: Maximum size of data that will be stored by any given USB interrupt.
    maximum_interrupt_size: Attribute[int] = attributes.AttrVI_ATTR_USB_MAX_INTR_SIZE()

    #: Manufacturer name.
    manufacturer_name: Attribute[str] = attributes.AttrVI_ATTR_MANF_NAME()

    #: Manufacturer identification number of the device.
    manufacturer_id: Attribute[int] = attributes.AttrVI_ATTR_MANF_ID()

    #: Model name of the device.
    model_name: Attribute[str] = attributes.AttrVI_ATTR_MODEL_NAME()

    #: Model code for the device.
    model_code: Attribute[int] = attributes.AttrVI_ATTR_MODEL_CODE()
```

[Source license and checked revision](../../pyvisa-source-license.md).
