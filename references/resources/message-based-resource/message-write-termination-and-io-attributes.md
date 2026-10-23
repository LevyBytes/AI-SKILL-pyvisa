# pyvisa.resources.messagebased.MessageBasedResource.write_termination

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    @write_termination.setter
    def write_termination(self, value: str) -> None:
        self._write_termination = value

    #: Should END be asserted during the transfer of the last byte of the buffer.
    send_end: Attribute[bool] = attributes.AttrVI_ATTR_SEND_END_EN()

    #: IO protocol to use. See the attribute definition for more details.
    io_protocol: Attribute[constants.IOProtocol] = attributes.AttrVI_ATTR_IO_PROT()

    #: Should I/O accesses use DMA (True) or Programmed I/O (False).
    allow_dma: Attribute[bool] = attributes.AttrVI_ATTR_DMA_ALLOW_EN()
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
