# pyvisa.highlevel.VisaLibraryBase.usb_control_out
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
usb_control_out(
    session: VISASession,
    request_type_bitmap_field: int,
    request_id: int,
    request_value: int,
    index: int,
    data: bytes = b'',
) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Perform a USB control pipe transfer to the device.

Corresponds to viUsbControlOut function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **request_type_bitmap_field** ([int](https://docs.python.org/3/library/functions.html#int)) – bmRequestType parameter of the setup stage of a USB control transfer.

- **request_id** ([int](https://docs.python.org/3/library/functions.html#int)) – bRequest parameter of the setup stage of a USB control transfer.

- **request_value** ([int](https://docs.python.org/3/library/functions.html#int)) – wValue parameter of the setup stage of a USB control transfer.

- **index** ([int](https://docs.python.org/3/library/functions.html#int)) – wIndex parameter for the setup stage of a USB control transfer. Usually identifies the interface or endpoint index.

- **data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes), optional) – Data buffer sent during the optional data stage of the control transfer.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

