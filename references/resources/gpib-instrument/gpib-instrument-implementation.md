# pyvisa.resources.gpib.GPIBInstrument

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](../gpib/gpib-module-imports-implementation.md)

```python
@Resource.register(constants.InterfaceType.gpib, "INSTR")
class GPIBInstrument(_GPIBMixin, MessageBasedResource):
    """Communicates with to devices of type GPIB::<primary address>[::INSTR]

    More complex resource names can be specified with the following grammar:
        GPIB[board]::primary address[::secondary address][::INSTR]

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    #: Whether to unaddress the device (UNT and UNL) after each read or write operation.
    enable_unaddressing: Attribute[bool] = attributes.AttrVI_ATTR_GPIB_UNADDR_EN()

    #: Whether to use repeat addressing before each read or write operation.
    enable_repeat_addressing: Attribute[bool] = attributes.AttrVI_ATTR_GPIB_READDR_EN()
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
