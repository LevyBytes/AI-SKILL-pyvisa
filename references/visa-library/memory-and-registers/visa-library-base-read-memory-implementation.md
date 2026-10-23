# pyvisa.highlevel.VisaLibraryBase.read_memory

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def read_memory(
        self,
        session: VISASession,
        space: constants.AddressSpace,
        offset: int,
        width: Union[Literal[8, 16, 32, 64], constants.DataWidth],
        extended: bool = False,
    ) -> Tuple[int, StatusCode]:
        """Read a value from the specified memory space and offset.

        Corresponds to viIn* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
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
        status_code : StatusCode
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
        return getattr(self, f"in_{w}")(session, space, offset, extended)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
