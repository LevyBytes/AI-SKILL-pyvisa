# pyvisa.constants.SerialTermination

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class SerialTermination(enum.IntEnum):
    """The available methods for terminating a serial transfer."""

    #: The transfer terminates when all requested data is transferred
    #: or when an error occurs.
    none = VI_ASRL_END_NONE

    #: The transfer occurs with the last bit not set until the last
    #: character is sent.
    last_bit = VI_ASRL_END_LAST_BIT

    #: The transfer terminate by searching for "/"
    #: appending the termination character.
    termination_char = VI_ASRL_END_TERMCHAR

    #: The write transmits a break after all the characters for the
    #: write are sent.
    termination_break = VI_ASRL_END_BREAK
```

[Source license and checked revision](../../pyvisa-source-license.md).
