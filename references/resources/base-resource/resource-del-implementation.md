# pyvisa.resources.resource.Resource.__del__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def __del__(self) -> None:
        if self._session is not None:
            try:
                self.close()
            except Exception:
                # Exceptions must be suppressed during __del__, because they
                # can't be caught by normal exception handling techniques and
                # get printed to stderr instead
                logger.warning(
                    "Exception suppressed while destroying a resource", exc_info=True
                )
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
