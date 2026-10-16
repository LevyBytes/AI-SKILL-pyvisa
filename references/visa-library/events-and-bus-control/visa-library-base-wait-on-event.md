# pyvisa.highlevel.VisaLibraryBase.wait_on_event
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
wait_on_event(
    session: VISASession,
    in_event_type: EventType,
    timeout: int,
) → Tuple[EventType, VISAEventContext, StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [EventType, VISAEventContext, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Wait for an occurrence of the specified event for a given session.

Corresponds to viWaitOnEvent function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **in_event_type** (constants.EventType) – Logical identifier of the event(s) to wait for.

- **timeout** ([int](https://docs.python.org/3/library/functions.html#int)) – Absolute wait time, in milliseconds, for the specified event before returning the time elapsed error.

Returns:

- constants.EventType – Logical identifier of the event actually received

- VISAEventContext – A handle specifying the unique occurrence of an event

- StatusCode – Return value of the library call.

