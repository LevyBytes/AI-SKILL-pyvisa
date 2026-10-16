# pyvisa.highlevel.VisaLibraryBase.usb_control_in

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def usb_control_in(
        self,
        session: VISASession,
        request_type_bitmap_field: int,
        request_id: int,
        request_value: int,
        index: int,
        length: int = 0,
    ) -> Tuple[bytes, StatusCode]:
        """Perform a USB control pipe transfer from the device.

        Corresponds to viUsbControlIn function of the VISA library.

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
        length : int, optional
            wLength parameter of the setup stage of a USB control transfer.
            This value also specifies the size of the data buffer to receive
            the data from the optional data stage of the control transfer.

        Returns
        -------
        bytes
            The data buffer that receives the data from the optional data stage
            of the control transfer
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
