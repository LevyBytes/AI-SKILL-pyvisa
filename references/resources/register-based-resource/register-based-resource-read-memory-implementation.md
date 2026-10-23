# pyvisa.resources.registerbased.RegisterBasedResource.read_memory

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](register-based-resource-implementation.md) / [Source module imports and declarations](registerbased-module-imports-implementation.md)

```python
    def read_memory(
        self,
        space: constants.AddressSpace,
        offset: int,
        width: constants.DataWidth,
        extended: bool = False,
    ) -> int:
        """Read a value from the specified memory space and offset.

        Parameters
        ----------
        space : constants.AddressSpace
            Specifies the address space from which to read.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        width : Union[Literal[8, 16, 32, 64], constants.DataWidth]
            Number of bits to read (8, 16, 32 or 64).
        extended : bool, optional
            Use 64 bits offset independent of the platform.

        Returns
        -------
        data : int
            Data read from memory

        Raises
        ------
        ValueError
            Raised if an invalid width is specified.

        """
        return self.visalib.read_memory(self.session, space, offset, width, extended)[0]
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
