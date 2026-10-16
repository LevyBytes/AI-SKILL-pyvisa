# VisaLibrary methods as way to call Visa functions
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

Historical migration guidance for PyVISA 1.5/1.6. Do not treat the old API names as current entrypoints.

### VisaLibrary methods as way to call Visa functions

Originally, PyVISA's `VisaLibrary` class mainly held a reference to the ctypes library plus a small set of functions.

Version 1.5 added the new `VisaLibrary` class (`pyvisa.highlevel`). It exposes every low level function defined in `ctwrapper` as a bound method, so code can call it this way:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager("/path/to/my/libvisa.so.7")
>>> lib = rm.visalib
>>> print(lib.read_stb(session))

```

(In most cases this is unnecessary, because the resource should already provide the function you need)

It also exposes every VISA foreign function from the underlying library as a static method, which lets you write code like this:

```python
>>> import ctypes
>>> status = ctypes.c_ushort()
>>> ret = lib.viReadSTB(session, ctypes.byref(status))
>>> print(status.value)  # ret is the VISA status code

```

