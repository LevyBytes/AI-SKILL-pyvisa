# pyvisa.highlevel.VisaLibraryBase.read_to_file

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def read_to_file(
        self, session: VISASession, filename: str, count: int
    ) -> Tuple[int, StatusCode]:
        """Read data synchronously, and store the transferred data in a file.

        Corresponds to viReadToFile function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        filename : str
            Name of file to which data will be written.
        count : int
            Number of bytes to be read.

        Returns
        -------
        int
            Number of bytes actually transferred
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
