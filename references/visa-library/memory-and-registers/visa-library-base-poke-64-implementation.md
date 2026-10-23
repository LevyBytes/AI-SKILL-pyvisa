# pyvisa.highlevel.VisaLibraryBase.poke_64

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def poke_64(
        self, session: VISASession, address: VISAMemoryAddress, data: int
    ) -> StatusCode:
        """Write an 64-bit value to the specified address.

        Corresponds to viPoke64 function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.
        data : int
            Data to write.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
