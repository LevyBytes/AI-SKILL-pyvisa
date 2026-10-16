# pyvisa.resources.resource.Resource.before_close

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def before_close(self) -> None:
        """Called just before closing an instrument."""
        self.__switch_events_off()
```

[Source license and checked revision](../../pyvisa-source-license.md).
