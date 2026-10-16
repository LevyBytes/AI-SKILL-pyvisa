# Configuring the backend
Context: PyVISA introduction-3; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](addresses-data-and-backends-index.md)

## Configuring the backend

### Configuring the backend

At present, two backends are available: the pyvisa backend that uses an IVI library (including NI-VISA, Keysight VISA, R&S VISA, tekVISA, etc.), and pyvisa-py, a pure python implementation of the VISA library. Without an explicit backend, pyvisa chooses the IVI backend when an IVI library is installed (details are in the next section); otherwise it falls back to pyvisa-py.

A backend can also be chosen by passing a parameter to ResourceManager; this example selects pyvisa-py:

```python
>>> pyvisa.ResourceManager('@py')

```

Another option is setting the PYVISA_LIBRARY environment variable, which accepts the same values as the ResourceManager constructor.

