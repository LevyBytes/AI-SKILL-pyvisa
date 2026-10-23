# pyvisa.resources.gpib.GPIBCommand.secondary_address

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](gpib-command-implementation.md) / [Source module imports and declarations](gpib-module-imports-implementation.md)

```python
    @staticmethod
    def secondary_address(device_sad) -> bytes:
        """MSA: MY SECONDARY ADDRESS

        For VISA SAD range from 1 to 31 and 0 is not SAD.

        WARNING: This is untested. We're assuming it to be 0x60 + device_sad,
        based on the pattern of 0x20 and 0x40 for the listener and talker addresses.

        """
        if device_sad == 0 or device_sad == constants.VI_NO_SEC_ADDR:
            return b""

        return (0x60 + device_sad).to_bytes(1, "big")

    MSA = secondary_address
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
