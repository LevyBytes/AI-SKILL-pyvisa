# pyvisa.resources.resource.Resource.session

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    @property
    def session(self) -> VISASession:
        """Resource session handle.

        Raises
        ------
        errors.InvalidSession
            Raised if session is closed.

        """
        if self._session is None:
            raise errors.InvalidSession()
        return self._session
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
