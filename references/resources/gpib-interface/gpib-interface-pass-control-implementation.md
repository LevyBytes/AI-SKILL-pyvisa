# pyvisa.resources.gpib.GPIBInterface.pass_control

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](gpib-interface-implementation.md) / [Source module imports and declarations](../gpib/gpib-module-imports-implementation.md)

```python
    def pass_control(
        self, primary_address: int, secondary_address: int
    ) -> constants.StatusCode:
        """Tell a GPIB device to become controller in charge (CIC).

        Corresponds to viGpibPassControl function of the VISA library.

        Parameters
        ----------
        primary_address : int
            Primary address of the GPIB device to which you want to pass control.
        secondary_address : int
            Secondary address of the targeted GPIB device.
            If the targeted device does not have a secondary address,
            this parameter should contain the value Constants.NO_SEC_ADDR.

        Returns
        -------
        constants.StatusCode
            Return value of the library call.

        """
        return self.visalib.gpib_pass_control(
            self.session, primary_address, secondary_address
        )
```

[Source license and checked revision](../../pyvisa-source-license.md).
