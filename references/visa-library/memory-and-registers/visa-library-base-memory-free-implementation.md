# pyvisa.highlevel.VisaLibraryBase.memory_free

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def memory_free(
        self, session: VISASession, offset: int, extended: bool = False
    ) -> StatusCode:
        """Frees memory previously allocated using the memory_allocation() operation.

        Corresponds to viMemFree* function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        offset : int
            Offset of the memory to free.
        extended : bool, optional
            Use 64 bits offset independent of the platform.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
