# pyvisa.highlevel.VisaLibraryBase.uninstall_visa_handler

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def uninstall_visa_handler(
        self,
        session: VISASession,
        event_type: constants.EventType,
        handler: VISAHandler,
        user_handle: Any = None,
    ) -> None:
        """Uninstalls handlers for events.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Logical event identifier.
        handler : VISAHandler
            Handler to be uninstalled by a client application.
        user_handle :
            The user handle returned by install_visa_handler.

        """
        for ndx, element in enumerate(self.handlers[session]):
            # use == rather than is to allow bound methods as handlers
            if (
                element[0] == handler
                and element[1] is user_handle
                and element[3] == event_type
            ):
                del self.handlers[session][ndx]
                break
        else:
            raise errors.UnknownHandler(event_type, handler, user_handle)
        self.uninstall_handler(session, event_type, element[2], user_handle)
```

[Source license and checked revision](../../pyvisa-source-license.md).
