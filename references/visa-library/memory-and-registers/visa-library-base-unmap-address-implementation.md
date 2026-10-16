# pyvisa.highlevel.VisaLibraryBase.unmap_address

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def unmap_address(self, session: VISASession) -> StatusCode:
        """Unmap memory space previously mapped by map_address().

        Corresponds to viUnmapAddress function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
