# pyvisa.highlevel.ResourceManager.last_status

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    @property
    def last_status(self) -> StatusCode:
        """Last status code returned for an operation with this Resource Manager."""
        return self.visalib.get_last_status_in_session(self.session)
```

[Source license and checked revision](../pyvisa-source-license.md).
