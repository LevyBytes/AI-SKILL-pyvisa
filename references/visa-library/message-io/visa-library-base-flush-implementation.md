# pyvisa.highlevel.VisaLibraryBase.flush

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def flush(
        self, session: VISASession, mask: constants.BufferOperation
    ) -> StatusCode:
        """Flush the specified buffers.

        The buffers can be associated with formatted I/O operations and/or
        serial communication.

        Corresponds to viFlush function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        mask : constants.BufferOperation
            Specifies the action to be taken with flushing the buffer.
            The values can be combined using the | operator. However multiple
            operations on a single buffer cannot be combined.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
