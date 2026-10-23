# pyvisa.highlevel.VisaLibraryBase.install_visa_handler

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def install_visa_handler(
        self,
        session: VISASession,
        event_type: constants.EventType,
        handler: VISAHandler,
        user_handle: Any = None,
    ) -> Any:
        """Installs handlers for event callbacks.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType,
            Logical event identifier.
        handler : VISAHandler
            Handler to be installed by a client application.
        user_handle :
            A value specified by an application that can be used for identifying
            handlers uniquely for an event type.

        Returns
        -------
        converted_user_handle:
            Converted user handle to match the underlying library. This version
            of the handle should be used in further call to the library.

        """
        try:
            new_handler = self.install_handler(
                session, event_type, handler, user_handle
            )
        except TypeError as e:
            raise errors.VisaTypeError(str(e)) from e

        self.handlers[session].append((*new_handler[:-1], event_type))
        return new_handler[1]
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
