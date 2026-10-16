# pyvisa.highlevel.ResourceManager.session

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    @property
    def session(self) -> VISARMSession:
        """Resource Manager session handle.

        Raises
        ------
        errors.InvalidSession
            Raised if the session is closed.

        """
        if self._session is None:
            raise errors.InvalidSession()
        return self._session
```

[Source license and checked revision](../pyvisa-source-license.md).
