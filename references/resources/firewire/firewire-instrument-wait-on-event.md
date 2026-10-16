# pyvisa.resources.FirewireInstrument.wait_on_event
Context: PyVISA pyvisa.resources.FirewireInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](firewire-instrument.md)

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

Maximum interval, expressed in time units, for the resource to wait for the requested event before it returns a timeout error. The unit is milliseconds. None indicates an unlimited wait when needed.

capture_timeoutbool, optional

When True, a VisaIOError(VI_ERROR_TMO) is suppressed; the call instead yields a WaitResponse where timed_out=True.

Returns:

Object that contains event_type, context and ret value.

Return type:

WaitResponse

