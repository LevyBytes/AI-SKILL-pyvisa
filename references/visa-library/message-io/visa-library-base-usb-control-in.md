# pyvisa.highlevel.VisaLibraryBase.usb_control_in
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
usb_control_in(
    session: VISASession,
    request_type_bitmap_field: int,
    request_id: int,
    request_value: int,
    index: int,
    length: int = 0,
) → Tuple[bytes, StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Perform a USB control pipe transfer from the device.

Corresponds to viUsbControlIn function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **request_type_bitmap_field** ([int](https://docs.python.org/3/library/functions.html#int)) – bmRequestType parameter of the setup stage of a USB control transfer.

- **request_id** ([int](https://docs.python.org/3/library/functions.html#int)) – bRequest parameter of the setup stage of a USB control transfer.

- **request_value** ([int](https://docs.python.org/3/library/functions.html#int)) – wValue parameter of the setup stage of a USB control transfer.

- **index** ([int](https://docs.python.org/3/library/functions.html#int)) – wIndex parameter for the setup stage of a USB control transfer. Usually identifies the interface or endpoint index.

- **length** ([int](https://docs.python.org/3/library/functions.html#int), optional) – wLength parameter for the setup stage of a USB control transfer. This value also gives the size of the data buffer used to receive data from the optional data stage of the control transfer.

Returns:

- bytes – Buffer populated by the optional data stage of the control transfer

- StatusCode – Return value of the library call.

