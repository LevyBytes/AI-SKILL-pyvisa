# pyvisa.highlevel.VisaLibraryBase.last_status

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    @property
    def last_status(self) -> StatusCode:
        """Last return value of the library."""
        return self._last_status
```

[Source license and checked revision](../../pyvisa-source-license.md).
