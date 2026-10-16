# Legacy migration: ResourceManager, discovery and low-level library
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md) / [Legacy migration: locks, termination and status access](legacy-locks-termination-and-status.md) / [Legacy migration: timeout units, formatting, delays and aliases](legacy-timeouts-formatting-and-aliases.md)

### Short summary

Through the legacy module, PyVISA 1.5 remains fully compatible with earlier PyVISA releases, although parts of the underlying implementation changed. To follow current development and stay compatible with PyVISA > 1.5, a few usage patterns should be updated.

PyVISA 1.6 does break compatibility, but those changes enable several useful improvements.

**If you are doing:**

```python
>>> import pyvisa
>>> keithley = pyvisa.instrument("GPIB::12")
>>> print(keithley.ask("*IDN?"))

```

change it to:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager()
>>> keithley = rm.open_resource("GPIB::12")
>>> print(keithley.query("*IDN?"))

```

**If you are doing:**

```python
>>> print(pyvisa.get_instruments_list())

```

change it to:

```python
>>> print(rm.list_resources())

```

**If you are doing:**

```python
>>> import pyvisa.vpp43 as vpp43
>>> vpp43.visa_library.load_library("/path/to/my/libvisa.so.7")

```

change it to:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager("/path/to/my/libvisa.so.7")
>>> lib = rm.visalib

```

