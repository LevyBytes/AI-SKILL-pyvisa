# pyvisa.highlevel.VisaLibraryBase.assert_utility_signal

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def assert_utility_signal(
        self, session: VISASession, line: constants.UtilityBusSignal
    ) -> StatusCode:
        """Assert or deassert the specified utility bus signal.

        Corresponds to viAssertUtilSignal function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        line : constants.UtilityBusSignal
            Specifies the utility bus signal to assert.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
