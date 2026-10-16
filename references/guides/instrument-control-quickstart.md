# PyVISA: Control your instruments with Python
Context: PyVISA latest; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](instrument-control-overview-index.md)

# Latest

> Pyvisa reference. Original prose; identifiers preserved verbatim.

### PyVISA: Control your instruments with Python

(Figure: PyVISA)

PyVISA is a Python package for driving measurement hardware of every sort, no matter which interface the gear speaks (e.g. GPIB, RS232, USB, Ethernet). To illustrate, querying the self-identification string of a Keithley Multimeter sitting at GPIB number 12 takes only three lines of Python:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager()
>>> rm.list_resources()
('ASRL1::INSTR', 'ASRL2::INSTR', 'GPIB0::12::INSTR')
>>> inst = rm.open_resource('GPIB0::12::INSTR')
>>> print(inst.query("*IDN?"))

```

(Yes, that snippet really is the entire program.) The package runs on Windows, Linux and Mac, and accepts adapters from any vendor (e.g. National Instruments, Agilent, Tektronix, Stanford Research Systems).

