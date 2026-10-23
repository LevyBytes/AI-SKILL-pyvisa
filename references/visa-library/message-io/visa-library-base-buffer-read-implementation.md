# pyvisa.highlevel.VisaLibraryBase.buffer_read

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def buffer_read(self, session: VISASession, count: int) -> Tuple[bytes, StatusCode]:
        """Reads data through the use of a formatted I/O read buffer.

        The data can be read from a device or an interface.

        Corresponds to viBufRead function of the VISA library.

        Parameters
        ----------
        session : VISASession\
            Unique logical identifier to a session.
        count : int
            Number of bytes to be read.

        Returns
        -------
        dbytes
            Data read
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
