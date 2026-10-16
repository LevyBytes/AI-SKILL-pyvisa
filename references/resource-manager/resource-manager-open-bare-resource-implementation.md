# pyvisa.highlevel.ResourceManager.open_bare_resource

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    def open_bare_resource(
        self,
        resource_name: str,
        access_mode: constants.AccessModes = constants.AccessModes.no_lock,
        open_timeout: int = constants.VI_TMO_IMMEDIATE,
    ) -> Tuple[VISASession, StatusCode]:
        """Open the specified resource without wrapping into a class.

        Parameters
        ----------
        resource_name : str
            Name or alias of the resource to open.
        access_mode : constants.AccessModes, optional
            Specifies the mode by which the resource is to be accessed,
            by default constants.AccessModes.no_lock
        open_timeout : int, optional
            If the ``access_mode`` parameter requests a lock, then this
            parameter specifies the absolute time period (in milliseconds) that
            the resource waits to get unlocked before this operation returns an
            error, by default constants.VI_TMO_IMMEDIATE.

        Returns
        -------
        VISASession
            Unique logical identifier reference to a session.
        StatusCode
            Return value of the library call.

        """
        return self.visalib.open(self.session, resource_name, access_mode, open_timeout)
```

[Source license and checked revision](../pyvisa-source-license.md).
