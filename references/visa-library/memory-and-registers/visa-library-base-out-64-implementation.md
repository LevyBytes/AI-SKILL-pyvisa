# pyvisa.highlevel.VisaLibraryBase.out_64

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def out_64(
        self,
        session: VISASession,
        space: constants.AddressSpace,
        offset: int,
        data: Iterable[int],
        extended: bool = False,
    ) -> StatusCode:
        """Write a 64-bit value to the specified memory space and offset.

        Corresponds to viOut64* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space into which to write.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        data : int
            Data to write to bus.
        extended : bool, optional
            Use 64 bits offset independent of the platform.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
