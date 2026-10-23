# pyvisa.resources.gpib.GPIBInterface.send_ifc

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](gpib-interface-implementation.md) / [Source module imports and declarations](../gpib/gpib-module-imports-implementation.md)

```python
    def send_ifc(self) -> constants.StatusCode:
        """Pulse the interface clear line (IFC) for at least 100 microseconds.

        Corresponds to viGpibSendIFC function of the VISA library.

        """
        return self.visalib.gpib_send_ifc(self.session)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
