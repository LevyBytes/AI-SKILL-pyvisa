# pyvisa.constants.AddressState

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class AddressState(enum.IntEnum):
    """State of a GPIB resource.

    Corresponds to the Attribute.GPIB_address_state attribute

    """

    #: The resource is unadressed
    unaddressed = VI_GPIB_UNADDRESSED

    #: The resource is addressed to talk
    talker = VI_GPIB_TALKER

    #: The resource is addressed to listen
    listenr = VI_GPIB_LISTENER
```

[Source license and checked revision](../../pyvisa-source-license.md).
