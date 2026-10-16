# pyvisa.constants.EventMechanism

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class EventMechanism(enum.IntEnum):
    """The available event mechanisms for event handling."""

    #: Queue events that can then be queried using wait_on_event
    queue = VI_QUEUE

    #: Use a specified callback handler to deal with events
    handler = VI_HNDLR

    #: Queue events to be passed to the handler when the system is switch to the
    #: handler mechanism.
    suspend_handler = VI_SUSPEND_HNDLR

    #: Use to disable or discard events no matter the handling mechanism
    all = VI_ALL_MECH


# Message based resources relevant constants
```

[Source license and checked revision](../../pyvisa-source-license.md).
