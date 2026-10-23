# pyvisa.highlevel.VisaLibraryBase.open_default_resource_manager

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def open_default_resource_manager(self) -> Tuple[VISARMSession, StatusCode]:
        """This function returns a session to the Default Resource Manager resource.

        Corresponds to viOpenDefaultRM function of the VISA library.

        Returns
        -------
        VISARMSession
            Unique logical identifier to a Default Resource Manager session
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
