# pyvisa.resources.resource.Resource.wrap_handler

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def wrap_handler(
        self, callable: Callable[["Resource", Event, Any], None]
    ) -> VISAHandler:
        """Wrap an event handler to provide the signature expected by VISA.

        The handler is expected to have the following signature:
        handler(resource: Resource, event: Event, user_handle: Any) -> None.

        The wrapped handler should be used only to handle events on the resource
        used to wrap the handler.

        """

        def event_handler(
            session: VISASession,
            event_type: constants.EventType,
            event_context: typing.VISAEventContext,
            user_handle: Any,
        ) -> None:
            if session != self.session:
                raise RuntimeError(
                    "When wrapping a handler, the resource used to wrap the handler"
                    "must be the same on which the handler will be installed."
                    f"Wrapping session: {self.session}, event on session: {session}"
                )
            event = Event(self.visalib, event_type, event_context)
            try:
                return callable(self, event, user_handle)
            finally:
                event.close()

        update_wrapper(event_handler, callable)

        return event_handler
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
