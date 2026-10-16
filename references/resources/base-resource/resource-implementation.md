# pyvisa.resources.resource.Resource

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
class Resource(object):
    """Base class for resources.

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    #: Reference to the resource manager used by this resource
    resource_manager: highlevel.ResourceManager

    #: Reference to the VISA library instance used by the resource
    visalib: highlevel.VisaLibraryBase

    #: VISA attribute descriptor classes that can be used to introspect the
    #: supported attributes and the possible values. The "often used" ones
    #: are generally directly available on the resource.
    visa_attributes_classes: ClassVar[Set[Type[attributes.Attribute]]]
```

[Source license and checked revision](../../pyvisa-source-license.md).
