# pyvisa.highlevel.VisaLibraryBase.gpib_control_ren

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def gpib_control_ren(
        self, session: VISASession, mode: constants.RENLineOperation
    ) -> StatusCode:
        """Controls the state of the GPIB Remote Enable (REN) interface line.

        Optionally the remote/local state of the device can also be set.

        Corresponds to viGpibControlREN function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        mode : constants.RENLineOperation
            State of the REN line and optionally the device remote/local state.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
