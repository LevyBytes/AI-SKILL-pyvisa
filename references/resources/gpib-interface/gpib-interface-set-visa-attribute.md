# pyvisa.resources.GPIBInterface.set_visa_attribute
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
set_visa_attribute(name: ResourceAttribute, state: Any) → StatusCode
```

Type and source details:

- [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Set an attribute state.

Prefer the dedicated descriptor for frequently used attributes because it validates and converts values automatically.

Parameters:

- **name** (constants.ResourceAttribute) – Attribute whose state should be changed.

- **state** (Any) – Attribute state to set on the specified object.

Returns:

Status returned by the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

