# pyvisa.highlevel.VisaLibraryBase.uninstall_handler

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def uninstall_handler(
        self,
        session: VISASession,
        event_type: constants.EventType,
        handler: VISAHandler,
        user_handle: Any = None,
    ) -> StatusCode:
        """Uninstall handlers for events.

        Corresponds to viUninstallHandler function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Logical event identifier.
        handler : VISAHandler
            Handler to be uninstalled by a client application.
        user_handle:
            A value specified by an application that can be used for
            identifying handlers uniquely in a session for an event.
            The modified value of the user_handle as returned by install_handler
            should be used instead of the original value.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
