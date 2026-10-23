# pyvisa.constants.Lock

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class Lock(enum.IntEnum):
    """Kind of lock to use when locking a resource."""

    #: Obtains a exclusive lock on the VISA resource.
    exclusive = VI_EXCLUSIVE_LOCK

    #: Obtains a lock on the VISA resouce which may be shared
    #: between multiple VISA sessions.
    shared = VI_SHARED_LOCK
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
