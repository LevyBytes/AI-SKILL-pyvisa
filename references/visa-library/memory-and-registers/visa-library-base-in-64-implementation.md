# pyvisa.highlevel.VisaLibraryBase.in_64

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def in_64(
        self,
        session: VISASession,
        space: constants.AddressSpace,
        offset: int,
        extended: bool = False,
    ) -> Tuple[int, StatusCode]:
        """Reads a 64-bit value at the given offset within the selected memory space.

        Corresponds to viIn64* function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Specifies the address space.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        extended : bool, optional
            Use 64 bits offset independent of the platform, False by default.

        Returns
        -------
        int
            Data read from memory
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
