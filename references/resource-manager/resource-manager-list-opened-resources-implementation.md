# pyvisa.highlevel.ResourceManager.list_opened_resources

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    def list_opened_resources(self) -> List["Resource"]:
        """Return a list of all the opened resources."""
        opened = []
        for resource in self._created_resources:
            try:
                resource.session
            except errors.InvalidSession:
                pass
            else:
                opened.append(resource)
        return opened
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
