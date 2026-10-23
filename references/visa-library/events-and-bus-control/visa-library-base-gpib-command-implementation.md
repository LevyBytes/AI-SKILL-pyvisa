# pyvisa.highlevel.VisaLibraryBase.gpib_command

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def gpib_command(self, session: VISASession, data: bytes) -> Tuple[int, StatusCode]:
        """Write GPIB command bytes on the bus.

        Corresponds to viGpibCommand function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        data : bytes
            Data to write.

        Returns
        -------
        int
            Number of written bytes
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
