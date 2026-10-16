# pyvisa.highlevel.VisaLibraryBase.poke

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def poke(
        self,
        session: VISASession,
        address: VISAMemoryAddress,
        width: Union[Literal[8, 16, 32, 64], constants.DataWidth],
        data: int,
    ) -> StatusCode:
        """Writes an 8, 16, 32, or 64-bit value from the specified address.

        Corresponds to viPoke* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.
        width : Union[Literal[8, 16, 32, 64], constants.DataWidth]
            Number of bits to read.
        data : int
            Data to write to the bus

        Returns
        -------
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
        return getattr(self, f"poke_{w}")(session, address, data)

    # Methods that VISA Library implementations must implement
```

[Source license and checked revision](../../pyvisa-source-license.md).
