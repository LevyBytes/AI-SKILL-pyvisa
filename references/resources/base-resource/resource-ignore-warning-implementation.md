# pyvisa.resources.resource.Resource.ignore_warning

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def ignore_warning(
        self, *warnings_constants: constants.StatusCode
    ) -> ContextManager:
        """Ignoring warnings context manager for the current resource.

        Parameters
        ----------
        warnings_constants : constants.StatusCode
            Constants identifying the warnings to ignore.

        """
        return self.visalib.ignore_warning(self.session, *warnings_constants)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
