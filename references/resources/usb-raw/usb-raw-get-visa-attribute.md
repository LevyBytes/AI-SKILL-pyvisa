# pyvisa.resources.USBRaw.get_visa_attribute
Context: PyVISA pyvisa.resources.USBRaw; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](usb-raw.md)

```text
get_visa_attribute(name: ResourceAttribute) → Any
```

Type and source details:

- [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Retrieves the state of an attribute in this resource.

For frequently used attributes, prefer the dedicated descriptor because it checks values and performs automatic conversion.

Parameters:

**name** (constants.ResourceAttribute) – Resource attribute for which the state query is made.

Returns:

The state of the queried attribute for a specified resource.

Return type:

Any

