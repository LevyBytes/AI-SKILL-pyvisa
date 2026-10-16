# pyvisa.resources.resource.Resource.disable_event

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def disable_event(
        self, event_type: constants.EventType, mechanism: constants.EventMechanism
    ) -> None:
        """Disable notification for an event type(s) via the specified mechanism(s).

        Parameters
        ----------
        event_type : constants.EventType
            Logical event identifier.
        mechanism : constants.EventMechanism
            Specifies event handling mechanisms to be disabled.

        """
        self.visalib.disable_event(self.session, event_type, mechanism)
```

[Source license and checked revision](../../pyvisa-source-license.md).
