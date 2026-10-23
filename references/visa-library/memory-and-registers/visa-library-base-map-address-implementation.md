# pyvisa.highlevel.VisaLibraryBase.map_address

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def map_address(
        self,
        session: VISASession,
        map_space: constants.AddressSpace,
        map_base: int,
        map_size: int,
        access: Literal[False] = False,
        suggested: Optional[int] = None,
    ) -> Tuple[int, StatusCode]:
        """Maps the specified memory space into the process's address space.

        Corresponds to viMapAddress function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        map_space : constants.AddressSpace
            Specifies the address space to map.
        map_base : int
            Offset (in bytes) of the memory to be mapped.
        map_size : int
            Amount of memory to map (in bytes).
        access : False
            Unused parameter.
        suggested : Optional[int], optional
            If not None, asks the operating system to map the memory at the
            requested address. That exact address is not guaranteed; this
            operation may place the memory in a different address region.

        Returns
        -------
        int
            Address in your process space where the memory was mapped
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
