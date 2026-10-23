# pyvisa.resources.registerbased.RegisterBasedResource.move_in

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](register-based-resource-implementation.md) / [Source module imports and declarations](registerbased-module-imports-implementation.md)

```python
    def move_in(
        self,
        space: constants.AddressSpace,
        offset: int,
        length: int,
        width: constants.DataWidth,
        extended: bool = False,
    ) -> List[int]:
        """Move a block of data to local memory from the given address space and offset.

        Corresponds to viMoveIn* functions of the VISA library.

        Parameters
        ----------
        space : constants.AddressSpace
            Address space from which to move the data.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        length : int
             Number of elements to transfer, where the data width of
             the elements to transfer is identical to the source data width.
        width : Union[Literal[8, 16, 32, 64], constants.DataWidth]
            Number of bits to read per element.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        data : List[int]
            Data read from the bus
        status_code : constants.StatusCode
            Return value of the library call.

        Raises
        ------
        ValueError
            Raised if an invalid width is specified.

        """
        return self.visalib.move_in(
            self.session, space, offset, length, width, extended
        )[0]
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
