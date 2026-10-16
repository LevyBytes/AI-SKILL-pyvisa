# pyvisa.resources.resource.Resource.discard_events

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def discard_events(
        self, event_type: constants.EventType, mechanism: constants.EventMechanism
    ) -> None:
        """Discards event occurrences for an event type and mechanism in this resource.

        Parameters
        ----------
        event_type : constants.EventType
            Logical event identifier.
        mechanism : constants.EventMechanism
            Specifies event handling mechanisms to be disabled.

        """
        self.visalib.discard_events(self.session, event_type, mechanism)
```

[Source license and checked revision](../../pyvisa-source-license.md).
