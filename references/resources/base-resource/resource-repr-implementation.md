# pyvisa.resources.resource.Resource.__repr__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def __repr__(self) -> str:
        return "<%r(%r)>" % (self.__class__.__name__, self._resource_name)
```

[Source license and checked revision](../../pyvisa-source-license.md).
