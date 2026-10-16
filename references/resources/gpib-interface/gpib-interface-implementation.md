# pyvisa.resources.gpib.GPIBInterface

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](../gpib/gpib-module-imports-implementation.md)

```python
@Resource.register(constants.InterfaceType.gpib, "INTFC")
class GPIBInterface(_GPIBMixin, MessageBasedResource):
    """Communicates with to devices of type GPIB::INTFC

    More complex resource names can be specified with the following grammar:
        GPIB[board]::INTFC

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    #: Is the specified GPIB interface currently the system controller.
    is_system_controller: Attribute[bool] = (
        attributes.AttrVI_ATTR_GPIB_SYS_CNTRL_STATE()
    )

    #: Is the specified GPIB interface currently CIC (Controller In Charge).
    is_controller_in_charge: Attribute[bool] = attributes.AttrVI_ATTR_GPIB_CIC_STATE()

    #: Current state of the GPIB ATN (ATtentioN) interface line.
    atn_state: Attribute[constants.LineState] = attributes.AttrVI_ATTR_GPIB_ATN_STATE()

    #: Current state of the GPIB NDAC (Not Data ACcepted) interface line.
    ndac_state: Attribute[constants.LineState] = (
        attributes.AttrVI_ATTR_GPIB_NDAC_STATE()
    )

    #: Is the GPIB interface currently addressed to talk or listen, or is not addressed.
    address_state: Attribute[constants.LineState] = (
        attributes.AttrVI_ATTR_GPIB_ADDR_STATE()
    )
```

[Source license and checked revision](../../pyvisa-source-license.md).
