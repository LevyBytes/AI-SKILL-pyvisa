# pyvisa.highlevel.VisaLibraryBase.read

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def read(self, session: VISASession, count: int) -> Tuple[bytes, StatusCode]:
        """Reads data from device or interface synchronously.

        Corresponds to viRead function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        count : int
            Number of bytes to be read.

        Returns
        -------
        bytes
            Date read
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
