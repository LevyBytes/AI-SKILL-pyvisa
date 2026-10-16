# pyvisa.resources.messagebased.MessageBasedResource.read_termination_context

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    @contextlib.contextmanager
    def read_termination_context(self, new_termination: Optional[str]) -> Iterator:
        term = self.read_termination
        self.read_termination = new_termination
        yield
        self.read_termination = term
```

[Source license and checked revision](../../pyvisa-source-license.md).
