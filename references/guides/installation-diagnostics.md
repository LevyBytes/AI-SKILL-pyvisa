# Testing your installation
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

### Testing your installation

That is it. To verify that PyVISA installed correctly, start python and create a ResourceManager:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager()
>>> print(rm.list_resources())

```

When a problem comes up, start with the [Miscellaneous questions](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#faq-faq), which collects common fixes and debugging techniques. If those do not resolve it, open an issue in the [issue tracker](https://github.com/pyvisa/pyvisa/issues)

