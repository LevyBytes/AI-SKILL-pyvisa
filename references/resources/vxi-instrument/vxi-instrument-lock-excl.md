# pyvisa.resources.VXIInstrument.lock_excl
Context: PyVISA pyvisa.resources.VXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-instrument.md)

```text
lock_excl(timeout: float | Literal['default'] = 'default') → None
```

Type and source details:

- [float](https://docs.python.org/3/library/functions.html#float)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [None](https://docs.python.org/3/library/constants.html#None)

Establish an exclusive lock to the resource.

Parameters:

**timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) - Allowed wait, in milliseconds, for release by the locking session before the resource returns an error. "default" means self.timeout is used.

