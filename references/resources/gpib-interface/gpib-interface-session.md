# pyvisa.resources.GPIBInterface.session
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
property session: VISASession
```

Resource session handle value.

Raises:

**errors.InvalidSession** – Raised when the session is closed.

