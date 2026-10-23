# pyvisa.highlevel.ResourceManager.last_status

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    @property
    def last_status(self) -> StatusCode:
        """Last status code returned for an operation with this Resource Manager."""
        return self.visalib.get_last_status_in_session(self.session)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
