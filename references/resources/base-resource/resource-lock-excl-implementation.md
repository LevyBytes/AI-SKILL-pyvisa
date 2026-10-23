# pyvisa.resources.resource.Resource.lock_excl

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def lock_excl(self, timeout: Union[float, Literal["default"]] = "default") -> None:
        """Establish an exclusive lock to the resource.

        Parameters
        ----------
        timeout : Union[float, Literal["default"]], optional
            Absolute time period (in milliseconds) that a resource waits to get
            unlocked by the locking session before returning an error.
            Defaults to "default" which means use self.timeout.

        """
        tout = cast(float, self.timeout if timeout == "default" else timeout)
        clean_timeout = util.cleanup_timeout(tout)
        self.visalib.lock(self.session, constants.Lock.exclusive, clean_timeout, None)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
