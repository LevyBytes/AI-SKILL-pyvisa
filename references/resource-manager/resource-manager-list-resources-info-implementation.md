# pyvisa.highlevel.ResourceManager.list_resources_info

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    def list_resources_info(self, query: str = "?*::INSTR") -> Dict[str, ResourceInfo]:
        """Get extended information about all connected devices matching query.

        For details of the VISA Resource Regular Expression syntax used in query,
        refer to list_resources().

        Returns
        -------
        Dict[str, ResourceInfo]
            Mapping of resource name to ResourceInfo

        """

        return {
            resource: self.resource_info(resource)
            for resource in self.list_resources(query)
        }
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
