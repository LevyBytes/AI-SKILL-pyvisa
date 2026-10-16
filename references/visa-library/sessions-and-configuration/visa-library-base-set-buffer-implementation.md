# pyvisa.highlevel.VisaLibraryBase.set_buffer

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def set_buffer(
        self, session: VISASession, mask: constants.BufferType, size: int
    ) -> StatusCode:
        """Sets the communication buffer size used for formatted I/O and/or low-level I/O.

        Corresponds to viSetBuf function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        mask : constants.BufferType
            Specifies the type of buffer.
        size : int
            The size to be set for the specified buffer(s).

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
