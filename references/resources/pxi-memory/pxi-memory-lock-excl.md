# pyvisa.resources.PXIMemory.lock_excl
Context: PyVISA pyvisa.resources.PXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-memory.md)

```text
lock_excl(timeout: float | Literal['default'] = 'default') → None
```

Type and source details:

- [float](https://docs.python.org/3/library/functions.html#float)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [None](https://docs.python.org/3/library/constants.html#None)

Establish an exclusive lock to the resource.

Parameters:

**timeout** (Union[[float](https://docs.python.org/3/library/functions.html#float), Literal["default"]], optional) - Maximum wait, in milliseconds, for the lock held by the locking session to clear before returning an error. "default" means self.timeout is used.

