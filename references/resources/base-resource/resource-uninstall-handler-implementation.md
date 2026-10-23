# pyvisa.resources.resource.Resource.uninstall_handler

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def uninstall_handler(
        self, event_type: constants.EventType, handler: VISAHandler, user_handle=None
    ) -> None:
        """Uninstalls handlers for events in this resource.

        Parameters
        ----------
        event_type : constants.EventType
            Logical event identifier.
        handler : VISAHandler
            Handler function to be uninstalled by a client application.
        user_handle : Any
            The user handle returned by install_handler.

        """
        self.visalib.uninstall_visa_handler(
            self.session, event_type, handler, user_handle
        )
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
