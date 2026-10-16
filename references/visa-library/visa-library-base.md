# pyvisa.highlevel.VisaLibraryBase
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](visa-library-base-low-level-api-index.md)



### Visa Library

```text
class pyvisa.highlevel.VisaLibraryBase(library_path: str | LibraryPath = '')
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)

Base for VISA library classes.

A class derived from VisaLibraryBase supplies low-level device communication through Pythonic wrappers around VISA functions. Derived classes may leave unsupported methods unimplemented. Methods normally return status codes, but on errors they should raise the matching exception because that is the Pythonic behavior.

The default VisaLibrary class is `pyvisa.ctwrapper.highlevel.IVIVisaLibrary`, a ctypes wrapper for the IVI-VISA library. IVI-VISA may be NI-VISA, Keysight VISA, R&S VISA, tekVISA, or another vendor implementation.

Usually, do not instantiate this object directly. User code normally works with [`pyvisa.highlevel.ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager). When necessary, retrieve the VISA library from that manager:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager("/path/to/my/libvisa.so.7")
>>> lib = rm.visalib

```

