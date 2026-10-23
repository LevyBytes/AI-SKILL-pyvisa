# pyvisa.highlevel.VisaLibraryBase.assert_trigger

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def assert_trigger(
        self, session: VISASession, protocol: constants.TriggerProtocol
    ) -> StatusCode:
        """Assert software or hardware trigger.

        Corresponds to viAssertTrigger function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        protocol : constants.TriggerProtocol
            Trigger protocol to use during assertion.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
