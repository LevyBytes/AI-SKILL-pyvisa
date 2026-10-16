# pyvisa.resources.resource.WaitResponse.__init__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](wait-response-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def __init__(
        self,
        event_type: constants.EventType,
        context: Optional[VISAEventContext],
        ret: constants.StatusCode,
        visalib: highlevel.VisaLibraryBase,
        timed_out: bool = False,
    ):
        self.event = Event(visalib, event_type, context)
        self._event_type = constants.EventType(event_type)
        self._context = context
        self.ret = ret
        self._visalib = visalib
        self.timed_out = timed_out
```

[Source license and checked revision](../../pyvisa-source-license.md).
