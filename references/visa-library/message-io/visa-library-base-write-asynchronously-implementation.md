# pyvisa.highlevel.VisaLibraryBase.write_asynchronously

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def write_asynchronously(
        self, session: VISASession, data: bytes
    ) -> Tuple[VISAJobID, StatusCode]:
        """Write data to device or interface asynchronously.

        Corresponds to viWriteAsync function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        data : bytes
            Data to be written.

        Returns
        -------
        VISAJobID
            Job ID of this asynchronous write operation
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
