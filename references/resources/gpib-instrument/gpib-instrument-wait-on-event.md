# pyvisa.resources.GPIBInstrument.wait_on_event
Context: PyVISA pyvisa.resources.GPIBInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-instrument.md)

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

Time in milliseconds that the resource waits for the requested event before returning a time elapsed error. None waits forever if necessary.

capture_timeoutbool, optional

When True, return a WaitResponse with timed_out=True instead of raising VisaIOError(VI_ERROR_TMO).

Returns:

Object that contains event_type, context and ret value.

Return type:

WaitResponse

