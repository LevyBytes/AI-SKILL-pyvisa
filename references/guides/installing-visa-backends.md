# Backend
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

### Backend

PyVISA requires a compatible backend before it can communicate with instruments. One bundled backend interfaces with the [National Instruments's VISA](https://www.ni.com/en-us/support/downloads/drivers/download.ni-visa.html) library, but that library must be downloaded and installed separately; see [NI-VISA Installation](https://pyvisa.readthedocs.io/en/latest/faq/getting_nivisa.html#faq-getting-nivisa). VISA libraries are provided by several vendors. PyVISA is tested with [National Instruments's VISA](https://www.ni.com/en-us/support/downloads/drivers/download.ni-visa.html) and [Keysight IO Library Suite](https://www.keysight.com/en/pd-1985909/io-libraries-suite/), both available at no cost, and you only need the driver library rather than a development environment.

Warning

PyVISA supports 32- and 64-bit Python and can use 32- and 64-bit VISA libraries without extra setup. It cannot mix bitness: 64-bit Python cannot load a 32-bit VISA library, and 32-bit Python cannot load a 64-bit VISA library.

**Python and the VISA library must use the same bitness**

Another option is [PyVISA-Py](http://pyvisa-py.readthedocs.io/en/latest/), a pure Python implementation of the VISA standard. Install it with [pip](http://www.pip-installer.org/):

```text
$ pip install -U pyvisa-py

```

Note

PyVISA-Py currently covers only part of the VISA standard, and protocol support varies by bus system. Check its documentation for the details.

