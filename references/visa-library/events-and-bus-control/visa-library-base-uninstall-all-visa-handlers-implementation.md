# pyvisa.highlevel.VisaLibraryBase.uninstall_all_visa_handlers

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def uninstall_all_visa_handlers(self, session: Optional[VISASession]) -> None:
        """Uninstalls all previously installed handlers for a particular session.

        Parameters
        ----------
        session : VISASession | None
            Unique logical identifier to a session. If None, operates on all sessions.

        """

        if session is not None:
            self.__uninstall_all_handlers_helper(session)
        else:
            for session in list(self.handlers):
                self.__uninstall_all_handlers_helper(session)
```

[Source license and checked revision](../../pyvisa-source-license.md).
