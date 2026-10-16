# pyvisa.resources.resource.Resource.resource_info

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    @property
    def resource_info(self) -> highlevel.ResourceInfo:
        """Get the extended information of this resource."""
        return self.visalib.parse_resource_extended(
            self._resource_manager.session, self._resource_name
        )[0]

    # --- VISA attributes --------------------------------------------------------------

    #: VISA attributes require the resource to be opened in order to get accessed.
    #: Please have a look at the attributes definition for more details

    # VI_ATTR_RM_SESSION is not implemented as resource property,
    # use .resource_manager.session instead
    # resource_manager_session: Attribute[int] = attributes.AttrVI_ATTR_RM_SESSION()

    #: Interface type of the given session.
    interface_type: Attribute[constants.InterfaceType] = (
        attributes.AttrVI_ATTR_INTF_TYPE()
    )

    #: Board number for the given interface.
    interface_number: Attribute[int] = attributes.AttrVI_ATTR_INTF_NUM()

    #: Resource class (for example, "INSTR") as defined by the canonical resource name.
    resource_class: Attribute[str] = attributes.AttrVI_ATTR_RSRC_CLASS()

    #: Unique identifier for a resource compliant with the address structure.
    resource_name: Attribute[str] = attributes.AttrVI_ATTR_RSRC_NAME()

    #: Resource version that identifies the revisions or implementations of a resource.
    implementation_version: Attribute[int] = attributes.AttrVI_ATTR_RSRC_IMPL_VERSION()

    #: Current locking state of the resource.
    lock_state: Attribute[constants.AccessModes] = (
        attributes.AttrVI_ATTR_RSRC_LOCK_STATE()
    )

    #: Version of the VISA specification to which the implementation is compliant.
    spec_version: Attribute[int] = attributes.AttrVI_ATTR_RSRC_SPEC_VERSION()

    #: Manufacturer name of the vendor that implemented the VISA library.
    resource_manufacturer_name: Attribute[str] = attributes.AttrVI_ATTR_RSRC_MANF_NAME()

    #: Timeout in milliseconds for all resource I/O operations.
    timeout: Attribute[float] = attributes.AttrVI_ATTR_TMO_VALUE()
```

[Source license and checked revision](../../pyvisa-source-license.md).
