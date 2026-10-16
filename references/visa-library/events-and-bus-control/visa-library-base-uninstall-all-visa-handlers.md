# pyvisa.highlevel.VisaLibraryBase.uninstall_all_visa_handlers
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
uninstall_all_visa_handlers(session: VISASession | None) → None
```

Type and source details:

- [None](https://docs.python.org/3/library/constants.html#None)

Uninstalls all previously installed handlers for a particular session.

Parameters:

**session** (VISASession | None) – Unique logical identifier for a session. If None, operates across all sessions.

