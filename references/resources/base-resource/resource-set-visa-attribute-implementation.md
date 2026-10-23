# pyvisa.resources.resource.Resource.set_visa_attribute

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def set_visa_attribute(
        self, name: constants.ResourceAttribute, state: Any
    ) -> constants.StatusCode:
        """Set the state of an attribute.

        One should prefer the dedicated descriptor for often used attributes
        since those perform checks and automatic conversion on the value.

        Parameters
        ----------
        name : constants.ResourceAttribute
            Attribute for which the state is to be modified.
        state : Any
            The state of the attribute to be set for the specified object.

        Returns
        -------
        constants.StatusCode
            Return value of the library call.

        """
        return self.visalib.set_attribute(self.session, name, state)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
