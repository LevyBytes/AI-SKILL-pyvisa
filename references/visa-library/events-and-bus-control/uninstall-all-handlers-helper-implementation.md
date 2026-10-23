# pyvisa.highlevel.VisaLibraryBase.__uninstall_all_handlers_helper

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def __uninstall_all_handlers_helper(self, session: VISASession) -> None:
        """Uninstall all VISA handlers for a given session."""
        for element in self.handlers[session]:
            self.uninstall_handler(session, element[3], element[2], element[1])
        del self.handlers[session]
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
