# pyvisa.resources.pxi.PXIBackplane

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](pxi-module-imports-implementation.md)

```python
@Resource.register(constants.InterfaceType.pxi, "BACKPLANE")
class PXIBackplane(RegisterBasedResource):
    """Communicates with to devices of type PXI[interface]::BACKPLANE

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    #: Manufacturer name.
    manufacturer_name: Attribute[str] = attributes.AttrVI_ATTR_MANF_NAME()

    #: Model name of the device.
    model_name: Attribute[str] = attributes.AttrVI_ATTR_MODEL_NAME()
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
