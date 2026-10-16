# pyvisa.highlevel.VisaLibraryBase.write_memory

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def write_memory(
        self,
        session: VISASession,
        space: constants.AddressSpace,
        offset: int,
        data: int,
        width: Union[Literal[8, 16, 32, 64], constants.DataWidth],
        extended: bool = False,
    ) -> StatusCode:
        """Write a value to the specified memory space and offset.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
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
        return getattr(self, f"out_{w}")(session, space, offset, data, extended)
```

[Source license and checked revision](../../pyvisa-source-license.md).
