# pyvisa.highlevel.VisaLibraryBase.vxi_command_query

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def vxi_command_query(
        self, session: VISASession, mode: constants.VXICommands, command: int
    ) -> Tuple[int, StatusCode]:
        """Send a miscellaneous command or query to the device and/or return the response from a previous query.

        Corresponds to viVxiCommandQuery function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        mode : constants.VXICommands
            Specifies whether to issue a command and/or retrieve a response.
        command : int
            The miscellaneous command to send.

        Returns
        -------
        int
            The response retrieved from the device
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
