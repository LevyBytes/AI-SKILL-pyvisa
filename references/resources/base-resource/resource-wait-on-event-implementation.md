# pyvisa.resources.resource.Resource.wait_on_event

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def wait_on_event(
        self,
        in_event_type: constants.EventType,
        timeout: int,
        capture_timeout: bool = False,
    ) -> WaitResponse:
        """Waits for an occurrence of the specified event in this resource.

        in_event_type : constants.EventType
            Logical identifier of the event(s) to wait for.
        timeout : int
            Absolute time period in time units that the resource shall wait for
            a specified event to occur before returning the time elapsed error.
            The time unit is in milliseconds. None means waiting forever if
            necessary.
        capture_timeout : bool, optional
            When True will not produce a VisaIOError(VI_ERROR_TMO) but instead
            return a WaitResponse with timed_out=True.

        Returns
        -------
        WaitResponse
            Object that contains event_type, context and ret value.

        """
        try:
            event_type, context, ret = self.visalib.wait_on_event(
                self.session, in_event_type, timeout
            )
        except errors.VisaIOError as exc:
            if capture_timeout and exc.error_code == constants.StatusCode.error_timeout:
                return WaitResponse(
                    in_event_type,
                    None,
                    constants.StatusCode.error_timeout,
                    self.visalib,
                    timed_out=True,
                )
            raise
        return WaitResponse(event_type, context, ret, self.visalib)
```

[Source license and checked revision](../../pyvisa-source-license.md).
