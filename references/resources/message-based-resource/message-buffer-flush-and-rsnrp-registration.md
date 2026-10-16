# pyvisa.resources.messagebased.MessageBasedResource.flush

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def flush(self, mask: constants.BufferOperation) -> None:
        """Manually clears the specified buffers.

        The mask value can make this write buffered data to the device.

        Parameters
        ----------
        mask : constants.BufferOperation
            Specifies the action to be taken with flushing the buffer.
            See highlevel.VisaLibraryBase.flush for a detailed description.

        """
        self.visalib.flush(self.session, mask)

# Rohde and Schwarz Device via Passport. Not sure which Resource should be.

MessageBasedResource.register(constants.InterfaceType.rsnrp, "INSTR")(
    MessageBasedResource
)
```

[Source license and checked revision](../../pyvisa-source-license.md).
