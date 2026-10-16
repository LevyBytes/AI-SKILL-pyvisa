# pyvisa.resources.Resource.visa_attributes_classes
Context: PyVISA pyvisa.resources.Resource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](resource.md)

```text
visa_attributes_classes: ClassVar[Set[Type[Attribute]]] = {
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
    <class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>,
    <class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>,
}
```

Type and source details:

- [ClassVar](https://docs.python.org/3/library/typing.html#typing.ClassVar)
- [Set](https://docs.python.org/3/library/typing.html#typing.Set)
- [Type](https://docs.python.org/3/library/typing.html#typing.Type)

Descriptor classes for VISA attributes; use them to inspect supported attributes and allowed values. Common descriptors are usually exposed directly on the resource.

