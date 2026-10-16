# pyvisa.highlevel.VisaLibraryBase.disable_event

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def disable_event(
        self,
        session: VISASession,
        event_type: constants.EventType,
        mechanism: constants.EventMechanism,
    ) -> StatusCode:
        """Disable notification for an event type(s) via the specified mechanism(s).

        Corresponds to viDisableEvent function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Event type.
        mechanism : constants.EventMechanism
            Event handling mechanisms to be disabled.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
