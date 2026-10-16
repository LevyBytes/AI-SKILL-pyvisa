# pyvisa.resources.MessageBasedResource.flush
Context: PyVISA pyvisa.resources.MessageBasedResource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](message-based-resource.md)

```text
flush(mask: BufferOperation) → None
```

Type and source details:

- [None](https://docs.python.org/3/library/constants.html#None)

Manually clears the specified buffers.

Some mask values also cause buffered data to be written out to the device.

Parameters:

**mask** (constants.BufferOperation) – Buffer-flush action to perform. See highlevel.VisaLibraryBase.flush for the full behavior.

