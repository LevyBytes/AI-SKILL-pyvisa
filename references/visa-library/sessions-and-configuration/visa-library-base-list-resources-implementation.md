# pyvisa.highlevel.VisaLibraryBase.list_resources

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def list_resources(
        self, session: VISARMSession, query: str = "?*::INSTR"
    ) -> Tuple[str, ...]:
        """Return a tuple of all connected devices matching query.

        Parameters
        ----------
        session : VISARMSession
            Unique logical identifier to the resource manager session.
        query : str
            Regular expression used to match devices.

        Returns
        -------
        Tuple[str, ...]
            Resource names of all the connected devices matching the query.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
