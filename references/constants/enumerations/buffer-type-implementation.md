# pyvisa.constants.BufferType

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class BufferType(enum.IntFlag):
    """Buffer potentially available on a message based resource.

    Used with the set_buffer function to alter the size of a buffer.

    """

    #: Formatted read buffer
    read = VI_READ_BUF

    #: Formatted write buffer
    write = VI_WRITE_BUF

    #: I/O communication receive buffer.
    io_in = VI_IO_IN_BUF

    #: I/O communication transmit buffer.
    io_out = VI_IO_OUT_BUF
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
