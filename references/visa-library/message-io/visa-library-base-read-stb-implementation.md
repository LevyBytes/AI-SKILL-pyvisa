# pyvisa.highlevel.VisaLibraryBase.read_stb

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def read_stb(self, session: VISASession) -> Tuple[int, StatusCode]:
        """Reads a status byte of the service request.

        Corresponds to viReadSTB function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.

        Returns
        -------
        int
            Service request status byte
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
