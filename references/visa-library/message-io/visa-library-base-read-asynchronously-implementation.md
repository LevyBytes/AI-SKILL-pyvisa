# pyvisa.highlevel.VisaLibraryBase.read_asynchronously

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def read_asynchronously(
        self, session: VISASession, count: int
    ) -> Tuple[SupportsBytes, VISAJobID, StatusCode]:
        """Reads data from device or interface asynchronously.

        Corresponds to viReadAsync function of the VISA library. Since the
        asynchronous operation may complete before the function call return
        implementation should make sure that get_buffer_from_id will be able
        to return the proper buffer before this method returns.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        count : int
            Number of bytes to be read.

        Returns
        -------
        SupportsBytes
            Buffer that will be filled during the asynchronous operation.
        VISAJobID
            Id of the asynchronous job
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
