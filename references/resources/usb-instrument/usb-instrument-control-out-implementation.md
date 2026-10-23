# pyvisa.resources.usb.USBInstrument.control_out

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](usb-instrument-implementation.md) / [Source module imports and declarations](../usb/usb-module-imports-implementation.md)

```python
    def control_out(
        self,
        request_type_bitmap_field: int,
        request_id: int,
        request_value: int,
        index: int,
        data: bytes = b"",
    ):
        """Performs a USB control pipe transfer to the device.

        Parameters
        ----------
        request_type_bitmap_field : int
            bmRequestType parameter of the setup stage of a USB control transfer.
        request_id : int
            bRequest parameter of the setup stage of a USB control transfer.
        request_value : int
            wValue parameter of the setup stage of a USB control transfer.
        index : int
            wIndex parameter of the setup stage of a USB control transfer.
            This is usually the index of the interface or endpoint.
        data : bytes
            The data buffer that sends the data in the optional data stage of
            the control transfer.

        """
        return self.visalib.usb_control_out(
            self.session,
            request_type_bitmap_field,
            request_id,
            request_value,
            index,
            data,
        )
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
