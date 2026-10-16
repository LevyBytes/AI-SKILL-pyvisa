# pyvisa.resources.resource.Resource.last_status

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    @property
    def last_status(self) -> constants.StatusCode:
        """Last status code for this session."""
        return self.visalib.get_last_status_in_session(self.session)
```

[Source license and checked revision](../../pyvisa-source-license.md).
