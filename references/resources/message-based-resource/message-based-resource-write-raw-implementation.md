# pyvisa.resources.messagebased.MessageBasedResource.write_raw

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def write_raw(self, message: bytes) -> int:
        """Write a byte message to the device.

        Parameters
        ----------
        message : bytes
            The message to be sent.

        Returns
        -------
        int
            Number of bytes written

        """
        return self.visalib.write(self.session, message)[0]
```

[Source license and checked revision](../../pyvisa-source-license.md).
