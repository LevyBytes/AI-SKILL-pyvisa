# pyvisa.highlevel.VisaLibraryBase.get_last_status_in_session

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def get_last_status_in_session(
        self, session: Union[VISASession, VISARMSession]
    ) -> StatusCode:
        """Last status in session.

        Helper function to be called by resources properties.

        """
        try:
            return self._last_status_in_session[session]
        except KeyError:
            raise errors.Error(
                "The session %r does not seem to be valid as it does not have any last status"
                % session
            )
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
