# pyvisa.constants.AddressSpace

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class AddressSpace(enum.IntEnum):
    """Address space for register based resources."""

    #: A16 address space of VXI/MXI bus.
    a16 = VI_A16_SPACE

    #: A24 address space of VXI/MXI bus.
    a24 = VI_A24_SPACE

    #: A32 address space of VXI/MXI bus.
    a32 = VI_A32_SPACE

    #: A64 address space of VXI/MXI bus.
    a64 = VI_A64_SPACE

    #: PCI configuration space.
    pxi_config = VI_PXI_CFG_SPACE

    #: Specified PCI memory or I/O space
    pxi_bar0 = VI_PXI_BAR0_SPACE
    pxi_bar1 = VI_PXI_BAR1_SPACE
    pxi_bar2 = VI_PXI_BAR2_SPACE
    pxi_bar3 = VI_PXI_BAR3_SPACE
    pxi_bar4 = VI_PXI_BAR4_SPACE
    pxi_bar5 = VI_PXI_BAR5_SPACE

    #: Physical locally allocated memory.
    pxi_allocated = VI_PXI_ALLOC_SPACE
```

[Source license and checked revision](../../pyvisa-source-license.md).
