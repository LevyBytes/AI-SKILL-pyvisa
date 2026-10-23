# pyvisa.constants.AccessModes

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class AccessModes(enum.IntEnum):
    """Whether and how to lock a resource when opening a connection."""

    #: Does not obtain any lock on the VISA resource.
    no_lock = VI_NO_LOCK

    #: Obtains a exclusive lock on the VISA resource.
    exclusive_lock = VI_EXCLUSIVE_LOCK

    #: Obtains a lock on the VISA resouce which may be shared
    #: between multiple VISA sessions.
    shared_lock = VI_SHARED_LOCK
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
