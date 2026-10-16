# pyvisa.resources.TCPIPSocket.get_visa_attribute
Context: PyVISA pyvisa.resources.TCPIPSocket; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](tcpip-socket.md)

```text
get_visa_attribute(name: ResourceAttribute) → Any
```

Type and source details:

- [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Retrieves the state of an attribute in this resource.

Prefer the dedicated descriptor for common attributes because it validates values and performs automatic conversions.

Parameters:

**name** (constants.ResourceAttribute) – Resource attribute for which the state query is made.

Returns:

The state of the queried attribute for a specified resource.

Return type:

Any

