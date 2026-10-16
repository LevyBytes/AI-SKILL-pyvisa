# pyvisa.resources.GPIBInterface.lock_excl
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
lock_excl(timeout: float | Literal['default'] = 'default') → None
```

Type and source details:

- [float](https://docs.python.org/3/library/functions.html#float)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [None](https://docs.python.org/3/library/constants.html#None)

Establish an exclusive lock to the resource.

Parameters:

**timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) – Time in milliseconds that the resource waits for the locking session to release it before an error is returned. The default is “default”, which uses self.timeout.

