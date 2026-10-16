# pyvisa.constants.USBEndInput

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class USBEndInput(enum.IntEnum):
    """Method used to terminate input on USB RAW."""

    none = VI_USB_END_NONE
    short = VI_USB_END_SHORT
    short_or_count = VI_USB_END_SHORT_OR_COUNT


# GPIB specific value
```

[Source license and checked revision](../../pyvisa-source-license.md).
