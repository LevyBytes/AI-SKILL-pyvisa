# pyvisa.highlevel.ResourceManager.__del__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    def __del__(self) -> None:
        if self._session is not None:
            self.close()
```

[Source license and checked revision](../pyvisa-source-license.md).
