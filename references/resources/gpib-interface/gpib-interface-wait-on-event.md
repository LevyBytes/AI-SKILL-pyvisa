# pyvisa.resources.GPIBInterface.wait_on_event
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
wait_on_event(
    in_event_type: EventType,
    timeout: int,
    capture_timeout: bool = False,
) → WaitResponse
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [bool](https://docs.python.org/3/library/functions.html#bool)

Wait for the specified event to occur on this resource.

in_event_typeconstants.EventType

Logical identifier for the event or events to wait on.

timeoutint

Absolute wait period before the resource reports a time elapsed error for the specified event. The unit is milliseconds. None waits indefinitely when needed.

capture_timeoutbool, optional

When True, a timeout returns a WaitResponse with timed_out=True instead of raising VisaIOError(VI_ERROR_TMO).

Returns:

Object containing event_type, context, and ret values.

Return type:

WaitResponse

