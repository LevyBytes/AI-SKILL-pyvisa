# pyvisa.highlevel.VisaLibraryBase.wait_on_event

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def wait_on_event(
        self, session: VISASession, in_event_type: constants.EventType, timeout: int
    ) -> Tuple[constants.EventType, VISAEventContext, StatusCode]:
        """Wait for an occurrence of the specified event for a given session.

        Corresponds to viWaitOnEvent function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        in_event_type : constants.EventType
            Logical identifier of the event(s) to wait for.
        timeout : int
            Absolute time period in time units that the resource shall wait for
            a specified event to occur before returning the time elapsed error.
            The time unit is in milliseconds.

        Returns
        -------
        constants.EventType
            Logical identifier of the event actually received
        VISAEventContext
            A handle specifying the unique occurrence of an event
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
