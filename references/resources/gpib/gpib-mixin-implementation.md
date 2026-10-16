# pyvisa.resources.gpib._GPIBMixin

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](gpib-module-imports-implementation.md)

```python
class _GPIBMixin(ControlRenMixin):
    """Common attributes and methods of GPIB Instr and Interface."""

    #: Primary address of the GPIB device used by the given session.
    primary_address: Attribute[int] = attributes.AttrVI_ATTR_GPIB_PRIMARY_ADDR()

    #: Secondary address of the GPIB device used by the given session.
    secondary_address: Attribute[int] = attributes.AttrVI_ATTR_GPIB_SECONDARY_ADDR()

    #: Current state of the GPIB REN (Remote ENable) interface line.
    remote_enabled: Attribute[constants.LineState] = (
        attributes.AttrVI_ATTR_GPIB_REN_STATE()
    )
```

[Source license and checked revision](../../pyvisa-source-license.md).
