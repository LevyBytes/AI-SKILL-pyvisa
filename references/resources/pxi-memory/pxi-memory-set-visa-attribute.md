# pyvisa.resources.PXIMemory.set_visa_attribute
Context: PyVISA pyvisa.resources.PXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-memory.md)

```text
set_visa_attribute(name: ResourceAttribute, state: Any) → StatusCode
```

Type and source details:

- [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Set the state of an attribute.

Prefer the dedicated descriptor for frequently used attributes, because it validates values and performs automatic conversion.

Parameters:

- **name** (constants.ResourceAttribute) – Attribute for which the state is to be modified.

- **state** (Any) - Value to assign as the attribute state on the specified object.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

