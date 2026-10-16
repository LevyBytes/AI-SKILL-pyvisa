# pyvisa.resources.VXIMemory.get_visa_attribute
Context: PyVISA pyvisa.resources.VXIMemory; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-memory.md)

```text
get_visa_attribute(name: ResourceAttribute) → Any
```

Type and source details:

- [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Retrieves the state of an attribute in this resource.

For attributes used often, prefer the dedicated descriptor; it validates values and applies automatic conversion.

Parameters:

**name** (constants.ResourceAttribute) – Resource attribute for which the state query is made.

Returns:

The state of the queried attribute for a specified resource.

Return type:

Any

