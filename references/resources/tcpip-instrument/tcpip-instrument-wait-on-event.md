# pyvisa.resources.TCPIPInstrument.wait_on_event
Context: PyVISA pyvisa.resources.TCPIPInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](tcpip-instrument.md)

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

Waits for an occurrence of the specified event in this resource.

in_event_typeconstants.EventType

Logical identifier of the event(s) to wait for.

timeoutint

Maximum wait, expressed in time units, for the requested event before a time-elapsed error is returned. The unit is milliseconds; None waits indefinitely when needed.

capture_timeoutbool, optional

When True, a timeout returns a WaitResponse with timed_out=True instead of raising VisaIOError(VI_ERROR_TMO).

Returns:

Object that contains event_type, context and ret value.

Return type:

WaitResponse

