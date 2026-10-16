# pyvisa.resources.resource.Resource.clear

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def clear(self) -> None:
        """Clear this resource."""
        self.visalib.clear(self.session)
```

[Source license and checked revision](../../pyvisa-source-license.md).
