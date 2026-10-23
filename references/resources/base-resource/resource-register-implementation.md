# pyvisa.resources.resource.Resource.register

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    @classmethod
    def register(
        cls, interface_type: constants.InterfaceType, resource_class: str
    ) -> Callable[[Type[T]], Type[T]]:
        """Create a decorator to register a class.

        The class is associated to an interface type, resource class pair.

        Parameters
        ----------
        interface_type : constants.InterfaceType
            Interface type for which to register a wrapper class.
        resource_class : str
            Resource class for which to register a wrapper class.

        Returns
        -------
        Callable[[Type[T]], Type[T]]
            Decorator registering the class. Raises TypeError if some VISA
            attributes are missing on the registered class.

        """

        def _internal(python_class):
            highlevel.ResourceManager.register_resource_class(
                interface_type, resource_class, python_class
            )

            return python_class

        return _internal
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
