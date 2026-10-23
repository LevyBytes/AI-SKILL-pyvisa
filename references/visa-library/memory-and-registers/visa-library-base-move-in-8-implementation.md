# pyvisa.highlevel.VisaLibraryBase.move_in_8

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def move_in_8(
        self,
        session: VISASession,
        space: constants.AddressSpace,
        offset: int,
        length: int,
        extended: bool = False,
    ) -> Tuple[List[int], StatusCode]:
        """Moves an 8-bit block of data to local memory.

        Corresponds to viMoveIn8* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space from which to move the data.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        length : int
             Number of elements to transfer, where the data width of
             the elements to transfer is identical to the source data width.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        data : List[int]
            Data read from the bus
        status_code : StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
