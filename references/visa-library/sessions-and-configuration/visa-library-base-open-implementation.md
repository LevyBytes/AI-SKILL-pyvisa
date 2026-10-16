# pyvisa.highlevel.VisaLibraryBase.open

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def open(
        self,
        session: VISARMSession,
        resource_name: str,
        access_mode: constants.AccessModes = constants.AccessModes.no_lock,
        open_timeout: int = constants.VI_TMO_IMMEDIATE,
    ) -> Tuple[VISASession, StatusCode]:
        """Opens a session to the specified resource.

        Corresponds to viOpen function of the VISA library.

        Parameters
        ----------
        session : VISARMSession
            Resource Manager session (should always be a session returned from
            open_default_resource_manager()).
        resource_name : str
            Unique symbolic name of a resource.
        access_mode : constants.AccessModes, optional
            Specifies the mode by which the resource is to be accessed.
        open_timeout : int
            If the ``access_mode`` parameter requests a lock, then this
            parameter specifies the absolute time period (in milliseconds) that
            the resource waits to get unlocked before this operation returns an
            error.

        Returns
        -------
        VISASession
            Unique logical identifier reference to a session
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
