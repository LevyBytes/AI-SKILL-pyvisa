# pyvisa.highlevel.VisaLibraryBase.gpib_pass_control

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def gpib_pass_control(
        self, session: VISASession, primary_address: int, secondary_address: int
    ) -> StatusCode:
        """Tell a GPIB device to become controller in charge (CIC).

        Corresponds to viGpibPassControl function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        primary_address : int
            Primary address for the GPIB device that will receive control.
        secondary_address : int
            Secondary address of the targeted GPIB device.
            If the targeted device does not have a secondary address, this parameter
            should contain the value Constants.VI_NO_SEC_ADDR.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
