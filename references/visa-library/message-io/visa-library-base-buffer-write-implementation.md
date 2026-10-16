# pyvisa.highlevel.VisaLibraryBase.buffer_write

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def buffer_write(self, session: VISASession, data: bytes) -> Tuple[int, StatusCode]:
        """Writes data to a formatted I/O write buffer synchronously.

        Corresponds to viBufWrite function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        data : bytes
            Data to be written.

        Returns
        -------
        int
            number of written bytes
        StatusCode
            return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
