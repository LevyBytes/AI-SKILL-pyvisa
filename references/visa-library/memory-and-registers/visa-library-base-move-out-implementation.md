# pyvisa.highlevel.VisaLibraryBase.move_out

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def move_out(
        self,
        session: VISASession,
        space: constants.AddressSpace,
        offset: int,
        length: int,
        data: Iterable[int],
        width: Union[Literal[8, 16, 32, 64], constants.DataWidth],
        extended: bool = False,
    ) -> StatusCode:
        """Move a block of data from local memory to the given address space and offset.

        Corresponds to viMoveOut* functions of the VISA library.

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
        width : Union[Literal[8, 16, 32, 64], constants.DataWidth]
            Number of bits to per element.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        StatusCode
            Return value of the library call.

        Raises
        ------
        ValueError
            Raised if an invalid width is specified.

        """
        w = width * 8 if isinstance(width, constants.DataWidth) else width
        if w not in (8, 16, 32, 64):
            raise ValueError(
                "%s is not a valid size. Valid values are 8, 16, 32 or 64 "
                "or one member of constants.DataWidth" % width
            )
        return getattr(self, f"move_out_{w}")(
            session, space, offset, length, data, extended
        )
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
