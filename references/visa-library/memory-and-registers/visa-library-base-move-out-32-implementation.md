# pyvisa.highlevel.VisaLibraryBase.move_out_32

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def move_out_32(
        self,
        session: VISASession,
        space: constants.AddressSpace,
        offset: int,
        length: int,
        data: Iterable[int],
        extended: bool = False,
    ) -> StatusCode:
        """Moves an 32-bit block of data from local memory.

        Corresponds to viMoveOut32* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space into which move the data.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        length : int
            Number of elements to transfer, where the data width of
            the elements to transfer is identical to the source data width.
        data : Iterable[int]
            Data to write to bus.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        StatusCode
            Return value of the library call.


        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
