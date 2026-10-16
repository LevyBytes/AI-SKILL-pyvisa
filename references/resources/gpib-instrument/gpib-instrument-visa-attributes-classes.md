# pyvisa.resources.GPIBInstrument.visa_attributes_classes
Context: PyVISA pyvisa.resources.GPIBInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-instrument.md)



```text
visa_attributes_classes: ClassVar[Set[Type[Attribute]]] = {
    <class 'pyvisa.attributes.AttrVI_ATTR_DMA_ALLOW_EN'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_FILE_APPEND_EN'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_PRIMARY_ADDR'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_READDR_EN'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_REN_STATE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_SECONDARY_ADDR'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_UNADDR_EN'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_INTF_INST_NAME'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_INTF_NUM'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_INTF_TYPE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_IO_PROT'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_MAX_QUEUE_LENGTH'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_OPER_MODE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_SIZE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RM_SESSION'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_CLASS'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_IMPL_VERSION'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_LOCK_STATE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_ID'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_NAME'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_NAME'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_SPEC_VERSION'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_SEND_END_EN'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_SUPPRESS_END_EN'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR_EN'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_TRIG_ID'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_OPER_MODE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_SIZE'>,
}
```

VISA attribute descriptor classes for inspecting supported attributes and allowed values. Commonly used attributes are usually exposed directly on the resource.

