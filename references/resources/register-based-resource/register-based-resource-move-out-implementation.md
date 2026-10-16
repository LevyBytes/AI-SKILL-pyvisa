# pyvisa.resources.registerbased.RegisterBasedResource.move_out

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](register-based-resource-implementation.md) / [Source module imports and declarations](registerbased-module-imports-implementation.md)

```python
    def move_out(
        self,
        space: constants.AddressSpace,
        offset: int,
        length: int,
        data: Iterable[int],
        width: constants.DataWidth,
        extended: bool = False,
    ) -> constants.StatusCode:
        """Move a block of data from local memory to the given address space and offset.

        Corresponds to viMoveOut* functions of the VISA library.

        Parameters
        ----------
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
        constants.StatusCode
            Return value of the library call.

        Raises
        ------
        ValueError
            Raised if an invalid width is specified.

        """
        return self.visalib.move_out(
            self.session, space, offset, length, data, width, extended
        )
```

[Source license and checked revision](../../pyvisa-source-license.md).
