# pyvisa.highlevel.ResourceManager.resource_info

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    def resource_info(self, resource_name: str, extended: bool = True) -> ResourceInfo:
        """Get the (extended) information of a particular resource.

        Parameters
        ----------
        resource_name : str
            Unique symbolic name of a resource.
        extended : bool, optional
            Also get extended information (ie. resource_class, resource_name, alias)

        """

        if extended:
            ret, _err = self.visalib.parse_resource_extended(
                self.session, resource_name
            )
        else:
            ret, _err = self.visalib.parse_resource(self.session, resource_name)

        return ret
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
