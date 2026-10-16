# pyvisa.resources.TCPIPInstrument.ignore_warning
Context: PyVISA pyvisa.resources.TCPIPInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](tcpip-instrument.md)

```text
ignore_warning(*warnings_constants: StatusCode) → ContextManager
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)
- [ContextManager](https://docs.python.org/3/library/typing.html#typing.ContextManager)

Ignoring warnings context manager for the current resource.

Parameters:

**warnings_constants** ([constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)) – Constants identifying the warnings to ignore.

