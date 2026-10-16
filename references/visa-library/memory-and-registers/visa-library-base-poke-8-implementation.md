# pyvisa.highlevel.VisaLibraryBase.poke_8

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def poke_8(
        self, session: VISASession, address: VISAMemoryAddress, data: int
    ) -> StatusCode:
        """Write an 8-bit value to the specified address.

        Corresponds to viPoke8 function of the VISA library.

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

[Source license and checked revision](../../pyvisa-source-license.md).
