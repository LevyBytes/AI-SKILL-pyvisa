# pyvisa.highlevel.VisaLibraryBase.map_trigger

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def map_trigger(
        self,
        session: VISASession,
        trigger_source: constants.InputTriggerLine,
        trigger_destination: constants.OutputTriggerLine,
        mode: None = None,
    ) -> StatusCode:
        """Map the specified trigger source line to the specified destination line.

        Corresponds to viMapTrigger function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        trigger_source : constants.InputTriggerLine
            Source line from which to map.
        trigger_destination : constants.OutputTriggerLine
            Destination line to which to map.
        mode : None, optional
            Always None for this version of the VISA specification.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
