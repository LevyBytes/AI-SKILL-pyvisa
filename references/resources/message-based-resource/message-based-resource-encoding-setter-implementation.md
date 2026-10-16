# pyvisa.resources.messagebased.MessageBasedResource.encoding

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    @encoding.setter
    def encoding(self, encoding: str) -> None:
        # Test that the encoding specified makes sense.
        "test encoding".encode(encoding).decode(encoding)
        self._encoding = encoding
```

[Source license and checked revision](../../pyvisa-source-license.md).
