# pyvisa.highlevel.ResourceManager.register_resource_class

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    @classmethod
    def register_resource_class(
        cls,
        interface_type: constants.InterfaceType,
        resource_class: str,
        python_class: Type["Resource"],
    ) -> None:
        """Register a class for a specific interface type, resource class pair.

        Parameters
        ----------
        interface_type : constants.InterfaceType
            Interface type for which to use the provided class.
        resource_class : str
            Resource class (INSTR, INTFC, ...)  for which to use the provided class.
        python_class : Type[Resource]
            Subclass of ``Resource`` to use when opening a resource matching the
            specified interface type and resource class.

        """
        if (interface_type, resource_class) in cls._resource_classes:
            logger.warning(
                "%s is already registered in the ResourceManager. "
                "Overwriting with %s" % ((interface_type, resource_class), python_class)
            )

        # If the class already has this attribute, it means that a parent class
        # was registered first. We need to copy the current set and extend it.
        attrs: Set[Type[attributes.Attribute]] = copy.copy(
            getattr(python_class, "visa_attributes_classes", set())
        )

        for attr in chain(
            attributes.AttributesPerResource[(interface_type, resource_class)],
            attributes.AttributesPerResource[attributes.AllSessionTypes],
        ):
            attrs.add(attr)
            # Error on non-properly set descriptor (this ensures that we are
            # consistent)
            if attr.py_name != "" and not hasattr(python_class, attr.py_name):
                raise TypeError(
                    "%s was expected to have a visa attribute %s"
                    % (python_class, attr.py_name)
                )

        setattr(python_class, "visa_attributes_classes", attrs)

        cls._resource_classes[(interface_type, resource_class)] = python_class
```

[Source license and checked revision](../pyvisa-source-license.md).
