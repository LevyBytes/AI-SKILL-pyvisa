# pyvisa.resources.gpib.GPIBCommand.talker

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](gpib-command-implementation.md) / [Source module imports and declarations](gpib-module-imports-implementation.md)

```python
    @staticmethod
    def talker(board_pad) -> bytes:
        """MTA: MY TALK ADDRESS."""
        return (0x40 + board_pad).to_bytes(1, "big")

    MTA = talker
```

[Source license and checked revision](../../pyvisa-source-license.md).
