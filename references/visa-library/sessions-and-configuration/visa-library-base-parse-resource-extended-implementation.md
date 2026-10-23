# pyvisa.highlevel.VisaLibraryBase.parse_resource_extended

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def parse_resource_extended(
        self, session: VISARMSession, resource_name: str
    ) -> Tuple[ResourceInfo, StatusCode]:
        """Parse a resource string to get extended interface information.

        Corresponds to viParseRsrcEx function of the VISA library.

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
        try:
            parsed = rname.parse_resource_name(resource_name)
        except ValueError:
            return (
                ResourceInfo(constants.InterfaceType.unknown, 0, None, None, None),
                StatusCode.error_invalid_resource_name,
            )

        board_number: Optional[int]
        try:
            # We can only get concrete classes which have one of those attributes
            board_number = int(
                parsed.board  # type: ignore
                if hasattr(parsed, "board")
                else parsed.interface  # type: ignore
            )
        # In some cases the board number may not be convertible to an int
        # PyVISA-py serial resources on Linux for example. For VICP, there is
        # no such attribute.
        except (ValueError, AttributeError):
            board_number = None

        return (
            ResourceInfo(
                parsed.interface_type_const,
                board_number,
                parsed.resource_class,
                str(parsed),
                None,
            ),
            StatusCode.success,
        )
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
