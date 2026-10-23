# pyvisa.highlevel.ResourceManager.close

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    def close(self) -> None:
        """Close the resource manager session.

        Notes
        -----
        Since the resource manager session is shared between instances
        this will also terminate connections obtained from other
        ResourceManager instances.

        """
        atexit.unregister(self._atexit_handler)
        try:
            logger.debug("Closing ResourceManager (session: %s)", self.session)
            # Cleanly close all resources when closing the manager.
            for resource in self._created_resources:
                resource.close()
            self.visalib.close(self.session)
            # mypy don't get that we can set a value we cannot get
            self.session = None  # type: ignore
            self.visalib.resource_manager = None
        except errors.InvalidSession:
            pass
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
