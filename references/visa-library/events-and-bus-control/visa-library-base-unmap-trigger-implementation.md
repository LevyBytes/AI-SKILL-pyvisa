# pyvisa.highlevel.VisaLibraryBase.unmap_trigger

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def unmap_trigger(
        self,
        session: VISASession,
        trigger_source: constants.InputTriggerLine,
        trigger_destination: constants.OutputTriggerLine,
    ) -> StatusCode:
        """Remove an existing trigger mapping from a source line to a destination line.

        Corresponds to viUnmapTrigger function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        trigger_source : constants.InputTriggerLine
            Source line used in previous map.
        trigger_destination : constants.OutputTriggerLine
            Destination line used in previous map.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
