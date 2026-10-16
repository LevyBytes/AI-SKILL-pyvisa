# pyvisa.highlevel.VisaLibraryBase.peek_32

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def peek_32(
        self, session: VISASession, address: VISAMemoryAddress
    ) -> Tuple[int, StatusCode]:
        """Read an 32-bit value from the specified address.

        Corresponds to viPeek32 function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.

        Returns
        -------
        int
            Data read from bus
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
