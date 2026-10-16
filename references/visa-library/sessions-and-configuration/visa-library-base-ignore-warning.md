# pyvisa.highlevel.VisaLibraryBase.ignore_warning
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
ignore_warning(session: VISASession | VISARMSession, *warnings_constants: StatusCode) → Iterator
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)
- [Iterator](https://docs.python.org/3/library/typing.html#typing.Iterator)

Ignore warnings for a session for the duration of the context.

Parameters:

- **session** (Union[VISASession, VISARMSession]) – Unique logical identifier to a session.

- **warnings_constants** ([StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)) – Constants identifying the warnings to ignore.

