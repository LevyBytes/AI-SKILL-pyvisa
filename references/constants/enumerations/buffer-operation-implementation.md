# pyvisa.constants.BufferOperation

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class BufferOperation(enum.IntFlag):
    """Possible action of the buffer when performing a flush."""

    #: Discard the read buffer contents and if data was present in the read buffer
    #: and no END-indicator was present, read from the device until encountering
    #: an END indicator (which causes the loss of data).
    discard_read_buffer = VI_READ_BUF

    #: Discard the read buffer contents (does not perform any I/O to the device).
    discard_read_buffer_no_io = VI_READ_BUF_DISCARD

    #: Flush the write buffer by writing all buffered data to the device.
    flush_write_buffer = VI_WRITE_BUF

    #: Discard the write buffer contents (does not perform any I/O to the device).
    discard_write_buffer = VI_WRITE_BUF_DISCARD

    #: Discard the receive buffer contents (does not perform any I/O to the device).
    discard_receive_buffer = VI_IO_IN_BUF_DISCARD

    #: Discards the receive buffer contents (same as VI_IO_IN_BUF_DISCARD)
    discard_receive_buffer2 = VI_IO_IN_BUF

    #: Flush the transmit buffer by writing all buffered data to the device.
    flush_transmit_buffer = VI_IO_OUT_BUF

    #: Discard the transmit buffer contents (does not perform any I/O to the device).
    discard_transmit_buffer = VI_IO_OUT_BUF_DISCARD


# Constants related to serial resources
```

[Source license and checked revision](../../pyvisa-source-license.md).
