# pyvisa.highlevel.ResourceManager.close
Context: PyVISA pyvisa.highlevel.ResourceManager; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../constants/constants-and-resource-manager-index.md) / [Owning VISA resource class and backend contract](resource-manager.md)

```text
close() → None
```

Type and source details:

- [None](https://docs.python.org/3/library/constants.html#None)

Close the resource manager session.

Notes

Because resource manager sessions are shared across instances, this also closes connections obtained from other ResourceManager instances.

