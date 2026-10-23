# pyvisa.resources.usb.USBInstrument.control_in

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](usb-instrument-implementation.md) / [Source module imports and declarations](../usb/usb-module-imports-implementation.md)

```python
    def control_in(
        self,
        request_type_bitmap_field: int,
        request_id: int,
        request_value: int,
        index: int,
        length: int = 0,
    ) -> bytes:
        """Performs a USB control pipe transfer from the device.

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
        length : int
            wLength parameter of the setup stage of a USB control transfer.
            This value also specifies the size of the data buffer to receive
            the data from the optional data stage of the control transfer.

        Returns
        -------
        bytes
            The data buffer that receives the data from the optional data stage
            of the control transfer.

        """
        return self.visalib.usb_control_in(
            self.session,
            request_type_bitmap_field,
            request_id,
            request_value,
            index,
            length,
        )[0]
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
