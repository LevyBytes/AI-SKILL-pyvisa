# pyvisa.resources.gpib.GPIBInterface.send_command

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](gpib-interface-implementation.md) / [Source module imports and declarations](../gpib/gpib-module-imports-implementation.md)

```python
    def send_command(self, data: bytes) -> Tuple[int, constants.StatusCode]:
        """Write GPIB command bytes on the bus.

        Corresponds to viGpibCommand function of the VISA library.

        Parameters
        ----------
        data : bytes
            Command to write.

        Returns
        -------
        int
            Number of bytes written
        constants.StatusCode
            Return value of the library call.

        """
        return self.visalib.gpib_command(self.session, data)
```

[Source license and checked revision](../../pyvisa-source-license.md).
