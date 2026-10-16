# pyvisa.highlevel.VisaLibraryBase.handlers
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
handlers: DefaultDict[VISASession, List[Tuple[Callable[[VISASession, EventType, VISAEventContext, Any], None], Any, Any, Any]]]
```

Type and source details:

- [DefaultDict](https://docs.python.org/3/library/typing.html#typing.DefaultDict)
- [VISASession, [List](https://docs.python.org/3/library/typing.html#typing.List)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)
- [VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [None](https://docs.python.org/3/library/constants.html#None)
- [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Contains all installed event handlers. Each entry is a four-element tuple: the handler itself as a Python callable, the user handle in a form meaningful to the lower-level implementation such as a ctypes object for the ctypes backend, the handler converted for backend use such as a CFUNCTYPE-created ctypes object for the ctypes backend, and the event type.

