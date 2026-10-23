# pyvisa.resources.resource.Resource.close

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def close(self) -> None:
        """Closes the VISA session and marks the handle as invalid."""
        try:
            logger.debug("%s - closing", self._resource_name, extra=self._logging_extra)
            self.before_close()
            self.visalib.close(self.session)
            # Mypy is confused by the idea that we can set a value we cannot get
            self.session = None  # type: ignore
        except errors.InvalidSession:
            pass

        logger.debug("%s - is closed", self._resource_name, extra=self._logging_extra)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
