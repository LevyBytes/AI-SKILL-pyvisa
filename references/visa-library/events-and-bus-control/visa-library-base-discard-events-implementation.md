# pyvisa.highlevel.VisaLibraryBase.discard_events

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def discard_events(
        self,
        session: VISASession,
        event_type: constants.EventType,
        mechanism: constants.EventMechanism,
    ) -> StatusCode:
        """Discard event occurrences for a given type and mechanisms in a session.

        Corresponds to viDiscardEvents function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Logical event identifier.
        mechanism : constants.EventMechanism
            Specifies event handling mechanisms to be discarded.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
