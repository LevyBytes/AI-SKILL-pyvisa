# pyvisa.highlevel.VisaLibraryBase.move

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def move(
        self,
        session: VISASession,
        source_space: constants.AddressSpace,
        source_offset: int,
        source_width: constants.DataWidth,
        destination_space: constants.AddressSpace,
        destination_offset: int,
        destination_width: constants.DataWidth,
        length: int,
    ) -> StatusCode:
        """Moves a block of data.

        Corresponds to viMove function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        source_space : constants.AddressSpace
            Specifies the address space of the source.
        source_offset : int
            Offset of the starting address or register from which to read.
        source_width : constants.DataWidth
            Specifies the data width of the source.
        destination_space : constants.AddressSpace
            Specifies the address space of the destination.
        destination_offset : int
            Offset of the starting address or register to which to write.
        destination_width : constants.DataWidth
            Specifies the data width of the destination.
        length: int
            Number of elements to transfer, where the data width of the
            elements to transfer is identical to the source data width.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
