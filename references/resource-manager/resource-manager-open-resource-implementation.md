# pyvisa.highlevel.ResourceManager.open_resource

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    def open_resource(
        self,
        resource_name: str,
        access_mode: constants.AccessModes = constants.AccessModes.no_lock,
        open_timeout: int = constants.VI_TMO_IMMEDIATE,
        resource_pyclass: Optional[Type["Resource"]] = None,
        **kwargs: Any,
    ) -> "Resource":
        """Return an instrument for the resource name.

        Parameters
        ----------
        resource_name : str
            Name or alias of the resource to open.
        access_mode : constants.AccessModes, optional
            Specifies the mode by which the resource is to be accessed,
            by default constants.AccessModes.no_lock
        open_timeout : int, optional
            If the ``access_mode`` parameter requests a lock, then this
            parameter specifies the absolute time period (in milliseconds) that
            the resource waits to get unlocked before this operation returns an
            error, by default constants.VI_TMO_IMMEDIATE.
        resource_pyclass : Optional[Type[Resource]], optional
            Resource Python class to use to instantiate the Resource.
            Defaults to None: select based on the resource name.
        kwargs : Any
            Keyword arguments to be used to change instrument attributes
            after construction.

        Returns
        -------
        Resource
            Subclass of Resource matching the resource.

        """
        if resource_pyclass is None:
            info = self.resource_info(resource_name, extended=True)

            try:
                # When using querying extended resource info the resource_class is not
                # None
                resource_pyclass = self._resource_classes[
                    (info.interface_type, info.resource_class)  # type: ignore
                ]
            except KeyError:
                resource_pyclass = self._resource_classes[
                    (constants.InterfaceType.unknown, "")
                ]
                logger.warning(
                    "There is no class defined for %r. Using Resource",
                    (info.interface_type, info.resource_class),
                )
        if hasattr(self.visalib, "open_resource"):
            res = self.visalib.open_resource(  # type: ignore
                resource_name, access_mode, open_timeout, resource_pyclass, **kwargs
            )
        else:
            res = resource_pyclass(self, resource_name)
            for key in kwargs.keys():
                try:
                    getattr(res, key)
                    present = True
                except AttributeError:
                    present = False
                except errors.InvalidSession:
                    present = True

                if not present:
                    raise ValueError(
                        "%r is not a valid attribute for type %s"
                        % (key, res.__class__.__name__)
                    )

            res.open(access_mode, open_timeout)

            for key, value in kwargs.items():
                setattr(res, key, value)

        self._created_resources.add(res)

        return res
```

[Source license and checked revision](../pyvisa-source-license.md).
