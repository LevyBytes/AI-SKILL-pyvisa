# pyvisa.highlevel.ResourceManager.__new__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    def __new__(
        cls: Type["ResourceManager"], visa_library: Union[str, VisaLibraryBase] = ""
    ) -> "ResourceManager":
        """Create a new resource manager tied to the specified VISA library.

        Parameters
        ----------
        visa_library : Union[str, VisaLibraryBase]
            Either a fully initialized VisaLibraryBase subclass instance or
            a str specification (see open_visa_library for the format).

        """
        if not isinstance(visa_library, VisaLibraryBase):
            visa_library = open_visa_library(visa_library)

        if visa_library.resource_manager is not None:
            obj = visa_library.resource_manager
            logger.debug("Reusing ResourceManager with session %s", obj.session)
            return obj

        obj = super(ResourceManager, cls).__new__(cls)

        obj.session, _err = visa_library.open_default_resource_manager()

        obj.visalib = visa_library
        obj.visalib.resource_manager = obj
        obj._created_resources = WeakSet()

        # Register an atexit handler to ensure the Resource Manager is properly
        # closed.
        close_ref = WeakMethod(obj.close)  # type: ignore

        def call_close():
            try:
                meth = close_ref()
                if meth:
                    meth()
            except Exception:
                # Suppress exceptions during exit
                logger.warning(
                    "Exception suppressed while closing a ResourceManager at system exit",
                    exc_info=True,
                )

        atexit.register(call_close)
        obj._atexit_handler = call_close  # type: ignore

        logger.debug("Created ResourceManager with session %s", obj.session)
        return obj
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
