# pyvisa.resources.resource.Resource.lock_context

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    @contextlib.contextmanager
    def lock_context(
        self,
        timeout: Union[float, Literal["default"]] = "default",
        requested_key: Optional[str] = "exclusive",
    ) -> Iterator[Optional[str]]:
        """A context that locks

        Parameters
        ----------
        timeout : Union[float, Literal["default"]], optional
            Absolute time period (in milliseconds) that a resource waits to get
            unlocked by the locking session before returning an error.
            Defaults to "default" which means use self.timeout.
        requested_key : Optional[str], optional
            When using default of 'exclusive' the lock is an exclusive lock.
            Otherwise it is the access key for the shared lock or None to
            generate a new shared access key.

        Yields
        ------
        Optional[str]
            The access_key if applicable.

        """
        if requested_key == "exclusive":
            self.lock_excl(timeout)
            access_key = None
        else:
            access_key = self.lock(timeout, requested_key)
        try:
            yield access_key
        finally:
            self.unlock()


Resource.register(constants.InterfaceType.unknown, "")(Resource)
```

[Source license and checked revision](../../pyvisa-source-license.md).
