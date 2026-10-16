# pyvisa.highlevel.ResourceManager

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md)

```python
class ResourceManager(object):
    """VISA Resource Manager."""

    #: Maps (Interface Type, Resource Class) to Python class encapsulating that resource.
    _resource_classes: ClassVar[
        Dict[Tuple[constants.InterfaceType, str], Type["Resource"]]
    ] = {}

    #: Session handler for the resource manager.
    _session: Optional[VISARMSession] = None

    #: Reference to the VISA library used by the ResourceManager
    visalib: VisaLibraryBase

    #: Resources created by this manager to allow closing them when the manager is closed
    _created_resources: WeakSet

    #: Handler for atexit using a weakref to close
    _atexit_handler: Callable
```

[Source license and checked revision](../pyvisa-source-license.md).
