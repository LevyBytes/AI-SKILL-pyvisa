# pyvisa.resources.gpib.GPIBInterface.control_atn

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](gpib-interface-implementation.md) / [Source module imports and declarations](../gpib/gpib-module-imports-implementation.md)

```python
    def control_atn(self, mode: constants.ATNLineOperation) -> constants.StatusCode:
        """Specifies the state of the ATN line and the local active controller state.

        Corresponds to viGpibControlATN function of the VISA library.

        Parameters
        ----------
        mode : constants.ATNLineOperation
            Specifies the state of the ATN line and optionally the local active
             controller state.

        Returns
        -------
        constants.StatusCode
            Return value of the library call.

        """
        return self.visalib.gpib_control_atn(self.session, mode)
```

[Source license and checked revision](../../pyvisa-source-license.md).
