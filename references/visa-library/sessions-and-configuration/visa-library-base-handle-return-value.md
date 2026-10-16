# pyvisa.highlevel.VisaLibraryBase.handle_return_value
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
handle_return_value(session: VISAEventContext | VISARMSession | VISASession | None, status_code: int) → StatusCode
```

Type and source details:

- [None](https://docs.python.org/3/library/constants.html#None)
- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Helper function handling the return code of a low-level operation.

Used when implementing concrete subclasses of VISALibraryBase.

