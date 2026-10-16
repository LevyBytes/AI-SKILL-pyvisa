# pyvisa.highlevel.ResourceManager.ignore_warning

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    def ignore_warning(self, *warnings_constants: StatusCode) -> ContextManager:
        """Ignoring warnings context manager for the current resource.

        Parameters
        ----------
        warnings_constants : StatusCode
            Constants identifying the warnings to ignore.

        """
        return self.visalib.ignore_warning(self.session, *warnings_constants)
```

[Source license and checked revision](../pyvisa-source-license.md).
