# Calling middle- and low-level functions
Context: PyVISA advanced; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](backend-development-index.md)

### Calling middle- and low-level functions

After creating a [`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager):

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager()

```

the related `VisaLibrary` instance is available through the `visalib` attribute.

For example, the VISA function `viMapAddress` is exposed in the low-level layer as the static method `viMapAddress` on the `visalib` attributed and in the middle-level layer as `map_address`.

The function names indicate which layer they belong to. Low-level functions keep the shared-library name and use the **vi** prefix. Middle-level functions use names that are more Pythonic but still recognizable: the leading **vi** is usually removed from camelCase names, then the remainder is converted to lowercase words separated by underscores. Documentation for these methods is in [API](https://pyvisa.readthedocs.io/en/latest/api/index.html#api).

