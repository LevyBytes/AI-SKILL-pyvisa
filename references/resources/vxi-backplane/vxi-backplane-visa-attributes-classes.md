# pyvisa.resources.VXIBackplane.visa_attributes_classes
Context: PyVISA pyvisa.resources.VXIBackplane; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-backplane.md)

```text
visa_attributes_classes: ClassVar[Set[Type[Attribute]]] = {
    <class 'pyvisa.attributes.AttrVI_ATTR_INTF_INST_NAME'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_INTF_NUM'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_INTF_PARENT_NUM'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_INTF_TYPE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_MAINFRAME_LA'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_MAX_QUEUE_LENGTH'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RM_SESSION'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_CLASS'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_IMPL_VERSION'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_LOCK_STATE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_ID'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_NAME'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_NAME'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_SPEC_VERSION'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_TRIG_ID'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_VXI_TRIG_STATUS'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_VXI_TRIG_SUPPORT'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_VXI_VME_INTR_STATUS'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_VXI_VME_SYSFAIL_STATE'>,
}
```

VISA attribute descriptor classes provide introspection for supported attributes and their possible values. The attributes used most often are generally available directly on the resource.

