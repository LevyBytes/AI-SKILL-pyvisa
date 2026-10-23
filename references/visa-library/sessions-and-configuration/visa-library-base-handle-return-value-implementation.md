# pyvisa.highlevel.VisaLibraryBase.handle_return_value

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def handle_return_value(
        self,
        session: Optional[Union[VISAEventContext, VISARMSession, VISASession]],
        status_code: int,
    ) -> StatusCode:
        """Helper function handling the return code of a low-level operation.

        Used when implementing concrete subclasses of VISALibraryBase.

        """
        rv: StatusCode
        try:
            rv = StatusCode(status_code)
        except ValueError:
            rv = cast(StatusCode, status_code)

        self._last_status = rv

        if session is not None:
            self._last_status_in_session[session] = rv

        if rv < 0:
            raise errors.VisaIOError(rv)

        if rv in self.issue_warning_on:
            if session and rv not in self._ignore_warning_in_session[session]:
                warnings.warn(errors.VisaIOWarning(rv), stacklevel=2)

        # Return the original value for further processing.
        return rv
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
