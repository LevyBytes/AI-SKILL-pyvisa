# pyvisa.resources.resource.Resource.get_visa_attribute

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def get_visa_attribute(self, name: constants.ResourceAttribute) -> Any:
        """Retrieves the state of an attribute in this resource.

        One should prefer the dedicated descriptor for often used attributes
        since those perform checks and automatic conversion on the value.

        Parameters
        ----------
        name : constants.ResourceAttribute
            Resource attribute for which the state query is made.

        Returns
        -------
        Any
            The state of the queried attribute for a specified resource.

        """
        return self.visalib.get_attribute(self.session, name)[0]
```

[Source license and checked revision](../../pyvisa-source-license.md).
