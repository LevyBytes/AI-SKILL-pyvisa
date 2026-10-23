# pyvisa.resources.registerbased.RegisterBasedResource.write_memory

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](register-based-resource-implementation.md) / [Source module imports and declarations](registerbased-module-imports-implementation.md)

```python
    def write_memory(
        self,
        space: constants.AddressSpace,
        offset: int,
        data: int,
        width: constants.DataWidth,
        extended: bool = False,
    ) -> constants.StatusCode:
        """Write a value to the specified memory space and offset.

        Parameters
        ----------
        space : constants.AddressSpace
            Specifies the address space.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        data : int
            Data to write to bus.
        width : Union[Literal[8, 16, 32, 64], constants.DataWidth]
            Number of bits to read.
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
        return self.visalib.write_memory(
            self.session, space, offset, data, width, extended
        )
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
