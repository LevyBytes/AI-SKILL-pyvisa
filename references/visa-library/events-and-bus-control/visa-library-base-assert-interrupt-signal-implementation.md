# pyvisa.highlevel.VisaLibraryBase.assert_interrupt_signal

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def assert_interrupt_signal(
        self,
        session: VISASession,
        mode: constants.AssertSignalInterrupt,
        status_id: int,
    ) -> StatusCode:
        """Asserts the specified interrupt or signal.

        Corresponds to viAssertIntrSignal function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        mode : constants.AssertSignalInterrupt
            How to assert the interrupt.
        status_id : int
            Status value to be presented during an interrupt acknowledge cycle.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
