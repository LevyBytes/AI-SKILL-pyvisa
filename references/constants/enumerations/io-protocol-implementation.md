# pyvisa.constants.IOProtocol

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class IOProtocol(enum.IntEnum):
    """IO protocol used for communication.

    See attributes.AttrVI_ATTR_IO_PROT for more details.

    """

    normal = VI_PROT_NORMAL

    #: Fast data channel (FDC) protocol for VXI
    fdc = VI_PROT_FDC

    #: High speed 488 transfer for GPIB
    hs488 = VI_PROT_HS488

    #: 488 style transfer for serial
    protocol4882_strs = VI_PROT_4882_STRS

    #: Test measurement class vendor specific for USB
    usbtmc_vendor = VI_PROT_USBTMC_VENDOR
```

[Source license and checked revision](../../pyvisa-source-license.md).
