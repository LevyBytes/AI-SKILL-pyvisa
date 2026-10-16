# A frontend for multiple backends
Context: PyVISA advanced; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](backend-development-index.md)

## A frontend for multiple backends

### A frontend for multiple backends

A short history helps explain this section. PyVISA began as a Python wrapper for the VISA library, more precisely a [`ctypes`](https://docs.python.org/3/library/ctypes.html#module-ctypes) wrapper around NI-VISA. That design worked, but it made alternative instrument communication paths hard to develop on platforms without NI-VISA. Users also had to change programs when switching to packages with different API.

Since 1.6, PyVISA has acted as a frontend to VISA. It offers a Pythonic API that can connect to several backends. Each backend provides a class derived from VisaLibraryBase to implement low-level communication. The default backend, called **ivi**, is the bundled ctypes wrapper around IVI-VISA. In practice, IVI-VISA may be NI-VISA, Keysight VISA, R&S VISA, tekVISA etc. By default, PyVISA calls whichever library is installed on the system as the VISA library.

Select the backend at resource manager creation time with the `@` symbol. Since **ivi** is the default, this:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager()

```

is equivalent to this:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager('@ivi')

```

If needed, you can still include the library path:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager('/path/to/lib@ivi')

```

Internally, [`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) locates the requested backend and instantiates the VISA library it supplies.

PyVISA resolves backends by name. With:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager('@somename')

```

PyVISA attempts to import an installed package/module named `pyvisa_somename` from your system. This keeps backend discovery loosely coupled and configuration free, because PyVISA only learns about a backend when you try to use it.

Run this command line code to list installed backends:

```console
pyvisa-info

```

