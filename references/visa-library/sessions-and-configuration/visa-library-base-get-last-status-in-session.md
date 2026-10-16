# pyvisa.highlevel.VisaLibraryBase.get_last_status_in_session
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
get_last_status_in_session(session: VISASession | VISARMSession) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Last status in session.

Helper function to be called by resources properties.

*static *get_library_paths() → [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[LibraryPath][source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.get_library_paths)

Override to list the possible library_paths if no path is specified.

