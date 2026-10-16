# pyvisa.resources.FirewireInstrument.get_visa_attribute
Context: PyVISA pyvisa.resources.FirewireInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](firewire-instrument.md)

```text
get_visa_attribute(name: ResourceAttribute) → Any
```

Type and source details:

- [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Retrieve an attribute state from this resource.

Prefer the dedicated descriptor for frequently used attributes because it validates and converts values automatically.

Parameters:

**name** (constants.ResourceAttribute) – Resource attribute whose state is queried.

Returns:

State value for the queried attribute on the specified resource.

Return type:

Any

