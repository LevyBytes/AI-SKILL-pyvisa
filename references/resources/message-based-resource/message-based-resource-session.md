# pyvisa.resources.MessageBasedResource.session
Context: PyVISA pyvisa.resources.MessageBasedResource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](message-based-resource.md)

```text
property session: VISASession
```

Resource session handle.

Raises:

**errors.InvalidSession** – Raised if session is closed.

