# pyvisa.resources.PXIInstrument.lock_excl
Context: PyVISA pyvisa.resources.PXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-instrument.md)

```text
lock_excl(timeout: float | Literal['default'] = 'default') → None
```

Type and source details:

- [float](https://docs.python.org/3/library/functions.html#float)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [None](https://docs.python.org/3/library/constants.html#None)

Establish an exclusive lock to the resource.

Parameters:

**timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) - Maximum wait, in milliseconds, for a locked resource to become available before an error is returned. Defaults to default, meaning self.timeout is used.

