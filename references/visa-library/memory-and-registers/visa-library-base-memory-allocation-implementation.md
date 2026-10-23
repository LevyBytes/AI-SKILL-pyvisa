# pyvisa.highlevel.VisaLibraryBase.memory_allocation

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def memory_allocation(
        self, session: VISASession, size: int, extended: bool = False
    ) -> Tuple[int, StatusCode]:
        """Allocate memory from a resource's memory region.

        Corresponds to viMemAlloc* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        size : int
            Specifies the size of the allocation.
        extended : bool, optional
            Use 64 bits offset independent of the platform.

        Returns
        -------
        int
            offset of the allocated memory
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
