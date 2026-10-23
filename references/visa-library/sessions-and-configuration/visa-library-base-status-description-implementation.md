# pyvisa.highlevel.VisaLibraryBase.status_description

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def status_description(
        self, session: VISASession, status: StatusCode
    ) -> Tuple[str, StatusCode]:
        """Return text that explains the supplied status code in a user-readable form.

        Corresponds to viStatusDesc function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        status : StatusCode
            Status code to interpret.

        Returns
        -------
        str
            User-readable string interpretation of the status code.
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
