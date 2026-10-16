# pyvisa.resources.messagebased.MessageBasedResource.stb

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    @property
    def stb(self) -> int:
        """Service request status register."""
        return self.read_stb()
```

[Source license and checked revision](../../pyvisa-source-license.md).
