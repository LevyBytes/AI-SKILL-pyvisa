# pyvisa.resources.messagebased.MessageBasedResource.assert_trigger

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def assert_trigger(self) -> None:
        """Sends a software trigger to the device."""
        self.visalib.assert_trigger(self.session, constants.TriggerProtocol.default)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
