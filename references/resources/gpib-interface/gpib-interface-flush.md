# pyvisa.resources.GPIBInterface.flush
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
flush(mask: BufferOperation) → None
```

Type and source details:

- [None](https://docs.python.org/3/library/constants.html#None)

Manually clears the specified buffers.

Depending on the mask value, this can write buffer data to the device.

Parameters:

**mask** (constants.BufferOperation) – Action used when flushing the buffer. See highlevel.VisaLibraryBase.flush for a detailed description.

