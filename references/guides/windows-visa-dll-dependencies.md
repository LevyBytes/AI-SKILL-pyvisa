# OSError: Could not open VISA library: function ‘viOpen’ not found
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

### OSError: Could not open VISA library: function ‘viOpen’ not found

On Windows, Python 3.8 changed how .dll files are loaded (see [https://docs.python.org/3/whatsnew/3.8.html#bpo-36085-whatsnew](https://docs.python.org/3/whatsnew/3.8.html#bpo-36085-whatsnew)). Because of that change, some Keysight VISA releases cannot locate required .dll dependencies during loading. To fix it, create a configuration file and set dll_extra_paths, as covered in [Configuring the backend](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html#intro-configuring).

