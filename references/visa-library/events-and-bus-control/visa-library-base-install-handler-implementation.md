# pyvisa.highlevel.VisaLibraryBase.install_handler

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def install_handler(
        self,
        session: VISASession,
        event_type: constants.EventType,
        handler: VISAHandler,
        user_handle: Any,
    ) -> Tuple[VISAHandler, Any, Any, StatusCode]:
        """Install handlers for event callbacks.

        Corresponds to viInstallHandler function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Logical event identifier.
        handler : VISAHandler
            Reference to a handler to be installed by a client application.
        user_handle : Any
            Value specified by an application that can be used for identifying
            handlers uniquely for an event type.

        Returns
        -------
        handler : VISAHandler
            Handler to be installed by a client application.
        converted_user_handle :
            Converted user handle to match the underlying library. This version
            of the handle should be used in further call to the library.
        converted_handler :
            Converted version of the handler satisfying to backend library.
        status_code : StatusCode
            Return value of the library call

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
