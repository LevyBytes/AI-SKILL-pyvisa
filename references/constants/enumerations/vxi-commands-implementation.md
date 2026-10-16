# pyvisa.constants.VXICommands

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class VXICommands(enum.IntEnum):
    """VXI commands that can be sent using the vxi_command_query."""

    #: Send a command fitting in a 16-bit integer
    command_16 = VI_VXI_CMD16

    #: Read a response fitting in a 16-bit integer
    response16 = VI_VXI_RESP16

    #: Send a command and read a response both fitting in a 16-bit integer
    command_response_16 = VI_VXI_CMD16_RESP16

    #: Send a command fitting in a 32-bit integer
    command_32 = VI_VXI_CMD32

    #: Read a response fitting in a 32-bit integer
    response32 = VI_VXI_RESP32

    #: Send a command and read a response both fitting in a 32-bit integer
    command_response_32 = VI_VXI_CMD32_RESP32

    #: Send a command (32-bit integer) and read a response (16-bit integer)
    command_32_response_16 = VI_VXI_CMD32_RESP16
```

[Source license and checked revision](../../pyvisa-source-license.md).
