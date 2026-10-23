# pyvisa.resources.resource.WaitResponse

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
class WaitResponse:
    """Class used in return of wait_on_event.

    It properly closes the context upon delete.

    A call with event_type of 0 (normally used when timed_out is True) will store
    None as the event and event type, otherwise it records the proper Event.

    """

    #: Reference to the event object that was waited for.
    event: Event

    #: Status code returned by the VISA library
    ret: constants.StatusCode

    #: Did a timeout occurs
    timed_out: bool
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
