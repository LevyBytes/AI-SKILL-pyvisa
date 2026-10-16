# pyvisa.resources.resource.WaitResponse.__del__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](wait-response-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def __del__(self) -> None:
        if self.event._context is not None:
            try:
                self._visalib.close(self.event._context)
                self.event.close()
            except errors.VisaIOError:
                pass


T = TypeVar("T", bound="Resource")
```

[Source license and checked revision](../../pyvisa-source-license.md).
