# Backend skeleton, required API and per-session status handling
Context: PyVISA advanced; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](backend-development-index.md) / [Complete backend level-2 implementation signature list](backend-method-signatures.md)

### Developing a new Backend

A minimum backend is quite small:

```python
from pyvisa.highlevel import VisaLibraryBase

class MyLibrary(VisaLibraryBase):
    pass

WRAPPER_CLASS = MyLibrary

```

You may also provide a staticmethod named get_debug_info that returns a dictionary of debug information printed by `pyvisa-info`

When developing a backend, one key decision is which VisaLibraryBase methods to implement and which API to expose.

A **complete** VISA Library implementation needs many functions, essentially nearly every level 2 function described in [Architecture](https://pyvisa.readthedocs.io/en/latest/advanced/architecture.html#advanced-architecture), with a full list at the end of this page. A usable implementation, however, does not have to provide all of them.

The **very minimum** set is:

- **open_default_resource_manager**: returns a session for the Default Resource Manager resource.

- **open**: Starts a session for the specified resource.

- **close**: Ends the specified session, event, or find list.

- **list_resources**: Returns a tuple containing every connected device that matches query.

(the signature is available below and in [Visa Library](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#api-visalibrarybase))

Note

[`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) checks for a `pyvisa.highlevel.VisaLibraryBase.open_resource` attribute so a new backend implementation can provide custom opening behavior.

That minimal set is not enough for much useful work. Commonly, you also need:

- **get_attribute**: Gets the current state of an attribute.

- **set_attribute**: Updates the state of an attribute.

To send bytes to MessageBased instruments, add:

- **read**: Synchronously reads data from a device or interface.

- **write**: Synchronously writes data to a device or interface.

Other devices or use cases may require additional functions; the exact set depends on your needs.

When appropriate, these functions should raise `pyvisa.errors.VisaIOError` or emit `pyvisa.errors.VisaIOWarning`, and they should store the error code per session. The simple way to do that is to call [`handle_return_value()`](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase.handle_return_value) with the session and return value.

