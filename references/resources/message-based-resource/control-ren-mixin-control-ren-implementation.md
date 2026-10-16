# pyvisa.resources.messagebased.ControlRenMixin.control_ren

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](control-ren-mixin-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def control_ren(self, mode: constants.RENLineOperation) -> constants.StatusCode:
        """Controls the state of the GPIB Remote Enable (REN) interface line.

        The remote/local state of the device can also be controlled optionally.

        Corresponds to viGpibControlREN function of the VISA library.

        Parameters
        ----------
        mode : constants.RENLineOperation
            Specifies the state of the REN line and optionally the device
            remote/local state.

        Returns
        -------
        constants.StatusCode
            Return value of the library call.

        """
        return self.visalib.gpib_control_ren(self.session, mode)
```

[Source license and checked revision](../../pyvisa-source-license.md).
