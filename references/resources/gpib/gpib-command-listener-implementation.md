# pyvisa.resources.gpib.GPIBCommand.listener

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](gpib-command-implementation.md) / [Source module imports and declarations](gpib-module-imports-implementation.md)

```python
    @staticmethod
    def listener(device_pad) -> bytes:
        """MLA: MY LISTEN ADDRESS."""
        return (0x20 + device_pad).to_bytes(1, "big")

    MLA = listener
```

[Source license and checked revision](../../pyvisa-source-license.md).
