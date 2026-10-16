# pyvisa.resources.SerialInstrument.xon_char
Context: PyVISA pyvisa.resources.SerialInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](serial-instrument.md)

```text
xon_char: Attribute[str]
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)

XON character for XON/XOFF flow control in both directions. The default character is 0x11.

