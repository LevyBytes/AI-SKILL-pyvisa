# pyvisa.highlevel.VisaLibraryBase.usb_control_out

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def usb_control_out(
        self,
        session: VISASession,
        request_type_bitmap_field: int,
        request_id: int,
        request_value: int,
        index: int,
        data: bytes = b"",
    ) -> StatusCode:
        """Perform a USB control pipe transfer to the device.

        Corresponds to viUsbControlOut function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        request_type_bitmap_field : int
            bmRequestType parameter of the setup stage of a USB control transfer.
        request_id : int
            bRequest parameter of the setup stage of a USB control transfer.
        request_value : int
            wValue parameter of the setup stage of a USB control transfer.
        index : int
            wIndex parameter of the setup stage of a USB control transfer.
            This is usually the index of the interface or endpoint.
        data : bytes, optional
            Data buffer used for the optional data stage of the control
            transfer.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
