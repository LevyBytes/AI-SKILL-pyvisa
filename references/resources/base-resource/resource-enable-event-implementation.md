# pyvisa.resources.resource.Resource.enable_event

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def enable_event(
        self,
        event_type: constants.EventType,
        mechanism: constants.EventMechanism,
        context: None = None,
    ) -> None:
        """Enable event occurrences for specified event types and mechanisms in this resource.

        Parameters
        ----------
        event_type : constants.EventType
            Logical event identifier.
        mechanism : constants.EventMechanism
            Specifies event handling mechanisms to be enabled
        context : None
            Not currently used, leave as None.

        """
        self.visalib.enable_event(self.session, event_type, mechanism, context)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
