# pyvisa.constants.ATNLineOperation

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class ATNLineOperation(enum.IntEnum):
    """Operation that can be performed on the GPIB ATN line.

    These operations are available only to GPIB INTFC resources

    """

    #: Assert ATN line synchronously (in 488 terminology). If a data handshake
    #: is in progress, ATN will not be asserted until the handshake is complete.
    asrt = VI_GPIB_ATN_ASSERT

    #: Assert ATN line asynchronously (in 488 terminology). This should generally
    #: be used only under error conditions.
    asrt_immediate = VI_GPIB_ATN_ASSERT_IMMEDIATE

    #: Deassert the ATN line
    deassert = VI_GPIB_ATN_DEASSERT

    #: Deassert ATN line, and enter shadow handshake mode. The local board will
    #: participate in data handshakes as an Acceptor without actually reading the data.
    deassert_handshake = VI_GPIB_ATN_DEASSERT_HANDSHAKE
```

[Source license and checked revision](../../pyvisa-source-license.md).
