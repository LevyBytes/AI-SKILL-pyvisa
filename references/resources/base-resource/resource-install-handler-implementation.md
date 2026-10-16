# pyvisa.resources.resource.Resource.install_handler

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def install_handler(
        self, event_type: constants.EventType, handler: VISAHandler, user_handle=None
    ) -> Any:
        """Install handlers for event callbacks in this resource.

        Parameters
        ----------
        event_type : constants.EventType
            Logical event identifier.
        handler : VISAHandler
            Handler function to be installed by a client application.
        user_handle :
            A value specified by an application that can be used for identifying
            handlers uniquely for an event type. Depending on the backend they
            may be restriction on the possible values. Look at the backend
            `install_visa_handler` for more details.

        Returns
        -------
        Any
            User handle in a format amenable to the backend. This is this
            representation of the handle that should be used when unistalling
            a handler.

        """
        return self.visalib.install_visa_handler(
            self.session, event_type, handler, user_handle
        )
```

[Source license and checked revision](../../pyvisa-source-license.md).
