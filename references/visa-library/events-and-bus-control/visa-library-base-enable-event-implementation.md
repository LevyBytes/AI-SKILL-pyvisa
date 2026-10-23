# pyvisa.highlevel.VisaLibraryBase.enable_event

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def enable_event(
        self,
        session: VISASession,
        event_type: constants.EventType,
        mechanism: constants.EventMechanism,
        context: None = None,
    ) -> StatusCode:
        """Enable event occurrences for specified event types and mechanisms in a session.

        Corresponds to viEnableEvent function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Logical event identifier.
        mechanism : constants.EventMechanism
            Specifies event handling mechanisms to be enabled.
        context : None, optional
            Unused parameter...

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
