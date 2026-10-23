# pyvisa.constants.LineState

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class LineState(enum.IntEnum):
    """State of a hardware line or signal.

    The line for which the state can be queried are:
    - ASRC resource: BREAK, CTS, DCD, DSR, DTR, RI, RTS signals
    - GPIB resources: ATN, NDAC, REN, SRQ lines
    - VXI BACKPLANE:  VXI/VME SYSFAIL backplane line

    Search for LineState in attributes.py for more details.

    """

    #: The line/signal is currently asserted
    asserted = VI_STATE_ASSERTED

    #: The line/signal is currently deasserted
    unasserted = VI_STATE_UNASSERTED

    #: The state of the line/signal is unknown
    unknown = VI_STATE_UNKNOWN
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
