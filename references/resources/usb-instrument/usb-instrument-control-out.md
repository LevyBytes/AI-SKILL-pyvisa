# pyvisa.resources.USBInstrument.control_out
Context: PyVISA pyvisa.resources.USBInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](usb-instrument.md)

```text
control_out(
    request_type_bitmap_field: int,
    request_id: int,
    request_value: int,
    index: int,
    data: bytes = b'',
)
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

Performs a USB control pipe transfer to the device.

Parameters:

- **request_type_bitmap_field** ([int](https://docs.python.org/3/library/functions.html#int)) – bmRequestType parameter of the setup stage of a USB control transfer.

- **request_id** ([int](https://docs.python.org/3/library/functions.html#int)) – bRequest parameter of the setup stage of a USB control transfer.

- **request_value** ([int](https://docs.python.org/3/library/functions.html#int)) – wValue parameter of the setup stage of a USB control transfer.

- **index** ([int](https://docs.python.org/3/library/functions.html#int)) – wIndex parameter for the setup stage of a USB control transfer. Usually this is the interface or endpoint index.

- **data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – Data buffer sent during the optional data stage of the control transfer.

