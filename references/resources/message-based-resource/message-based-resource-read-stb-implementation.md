# pyvisa.resources.messagebased.MessageBasedResource.read_stb

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def read_stb(self) -> int:
        """Service request status register."""
        value, _retcode = self.visalib.read_stb(self.session)
        return value
```

[Source license and checked revision](../../pyvisa-source-license.md).
