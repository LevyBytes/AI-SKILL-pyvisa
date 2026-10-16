# pyvisa.resources.resource.Resource.__switch_events_off

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def __switch_events_off(self) -> None:
        """Switch off and discards all events."""
        self.disable_event(
            constants.EventType.all_enabled, constants.EventMechanism.all
        )
        self.discard_events(
            constants.EventType.all_enabled, constants.EventMechanism.all
        )
        self.visalib.uninstall_all_visa_handlers(self.session)
```

[Source license and checked revision](../../pyvisa-source-license.md).
