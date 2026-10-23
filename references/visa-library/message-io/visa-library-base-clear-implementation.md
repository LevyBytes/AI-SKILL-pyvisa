# pyvisa.highlevel.VisaLibraryBase.clear

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def clear(self, session: VISASession) -> StatusCode:
        """Clears a device.

        Corresponds to viClear function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
