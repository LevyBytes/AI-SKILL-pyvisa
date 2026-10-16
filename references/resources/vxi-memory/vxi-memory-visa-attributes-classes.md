# pyvisa.resources.VXIMemory.visa_attributes_classes
Context: PyVISA pyvisa.resources.VXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-memory.md)

```text
visa_attributes_classes: ClassVar[Set[Type[Attribute]]] = {
    <class 'pyvisa.attributes.AttrVI_ATTR_DEST_ACCESS_PRIV'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_DEST_BYTE_ORDER'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_DEST_INCREMENT'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_DMA_ALLOW_EN'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_INTF_INST_NAME'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_INTF_NUM'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_INTF_TYPE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_MAX_QUEUE_LENGTH'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RM_SESSION'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_CLASS'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_IMPL_VERSION'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_LOCK_STATE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_ID'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_NAME'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_NAME'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_SPEC_VERSION'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_SRC_ACCESS_PRIV'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_SRC_BYTE_ORDER'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_SRC_INCREMENT'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_VXI_LA'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_WIN_ACCESS'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_WIN_ACCESS_PRIV'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_WIN_BASE_ADDR'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_WIN_BYTE_ORDER'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_WIN_SIZE'>,
}
```

VISA attribute descriptor classes let code inspect supported attributes and the values they may accept. Frequently used attributes are usually exposed directly on the resource.

