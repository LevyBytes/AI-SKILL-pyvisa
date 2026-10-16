# pyvisa.highlevel.ResourceManager.session
Context: PyVISA pyvisa.highlevel.ResourceManager; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../constants/constants-and-resource-manager-index.md) / [Owning VISA resource class and backend contract](resource-manager.md)

```text
property session: VISARMSession
```

Resource Manager session handle.

Raises:

**errors.InvalidSession** - Raised when the session is closed.
