# pyvisa.resources.resource.Resource.__init__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def __init__(
        self, resource_manager: highlevel.ResourceManager, resource_name: str
    ) -> None:
        self._resource_manager = resource_manager
        self.visalib = self._resource_manager.visalib

        # We store the resource name and use preferably the private attr over
        # the public descriptor internally because the public descriptor
        # requires a live instance the VISA library, which means it is much
        # slower but also can cause issue in error reporting when accessing the
        # repr
        self._resource_name: str
        try:
            # Attempt to normalize the resource name. Can fail for aliases
            self._resource_name = str(rname.ResourceName.from_string(resource_name))
        except rname.InvalidResourceName:
            self._resource_name = resource_name

        self._logging_extra = {
            "library_path": self.visalib.library_path,
            "resource_manager.session": self._resource_manager.session,
            "resource_name": self._resource_name,
            "session": None,
        }

        #: Session handle.
        self._session: Optional[VISASession] = None
```

[Source license and checked revision](../../pyvisa-source-license.md).
