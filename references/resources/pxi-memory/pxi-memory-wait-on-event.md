# pyvisa.resources.PXIMemory.wait_on_event
Context: PyVISA pyvisa.resources.PXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-memory.md)

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

Absolute timeout, expressed in milliseconds, for how long the resource waits for the requested event before returning a time elapsed error. None indicates that it may wait indefinitely.

capture_timeoutbool, optional

If True, the call returns a WaitResponse with timed_out=True instead of raising VisaIOError(VI_ERROR_TMO).

Returns:

Object that contains event_type, context and ret value.

Return type:

WaitResponse

