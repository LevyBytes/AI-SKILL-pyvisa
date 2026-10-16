# pyvisa.constants.LineState
Context: PyVISA pyvisa.constants.LineState; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../constants-and-resource-manager-index.md)

```text
class pyvisa.constants.LineState(value)
```

Represents the state of a hardware line or signal.

Queryable states include these lines: - ASRC resource signals: BREAK, CTS, DCD, DSR, DTR, RI, RTS - GPIB resources lines: ATN, NDAC, REN, SRQ - VXI BACKPLANE line: VXI/VME SYSFAIL backplane line

For additional details, search for LineState in attributes.py.

