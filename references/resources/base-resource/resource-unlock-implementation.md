# pyvisa.resources.resource.Resource.unlock

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def unlock(self) -> None:
        """Relinquishes a lock for the specified resource."""
        self.visalib.unlock(self.session)
```

[Source license and checked revision](../../pyvisa-source-license.md).
