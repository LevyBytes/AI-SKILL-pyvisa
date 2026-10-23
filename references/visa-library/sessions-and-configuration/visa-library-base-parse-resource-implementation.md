# pyvisa.highlevel.VisaLibraryBase.parse_resource

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def parse_resource(
        self, session: VISARMSession, resource_name: str
    ) -> Tuple[ResourceInfo, StatusCode]:
        """Parse a resource string to get the interface information.

        Corresponds to viParseRsrc function of the VISA library.

        Parameters
        ----------
        session : VISARMSession
            Resource Manager session (should always be the Default Resource
            Manager for VISA returned from open_default_resource_manager()).
        resource_name : str
             Unique symbolic name of a resource.

        Returns
        -------
        ResourceInfo
            Resource information with interface type and board number
        StatusCode
            Return value of the library call.

        """
        ri, status = self.parse_resource_extended(session, resource_name)
        if status == StatusCode.success:
            return (
                ResourceInfo(
                    ri.interface_type, ri.interface_board_number, None, None, None
                ),
                StatusCode.success,
            )
        else:
            return ri, status
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
