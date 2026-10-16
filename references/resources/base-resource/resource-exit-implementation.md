# pyvisa.resources.resource.Resource.__exit__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def __exit__(self, *args) -> None:
        self.close()
```

[Source license and checked revision](../../pyvisa-source-license.md).
