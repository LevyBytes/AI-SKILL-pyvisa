# pyvisa.highlevel.VisaLibraryBase.gpib_send_ifc

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def gpib_send_ifc(self, session: VISASession) -> StatusCode:
        """Pulse the interface clear line (IFC) for at least 100 microseconds.

        Corresponds to viGpibSendIFC function of the VISA library.

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

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
