# pyvisa.highlevel.VisaLibraryBase.ignore_warning

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    @contextlib.contextmanager
    def ignore_warning(
        self,
        session: Union[VISASession, VISARMSession],
        *warnings_constants: StatusCode,
    ) -> Iterator:
        """Ignore warnings for a session for the duration of the context.

        Parameters
        ----------
        session : Union[VISASession, VISARMSession]
            Unique logical identifier to a session.
        warnings_constants : StatusCode
            Constants identifying the warnings to ignore.

        """
        self._ignore_warning_in_session[session].update(warnings_constants)
        yield
        self._ignore_warning_in_session[session].difference_update(warnings_constants)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
