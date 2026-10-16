# pyvisa.highlevel.VisaLibraryBase.set_attribute
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
set_attribute(
    session: VISASession,
    attribute: ResourceAttribute,
    attribute_state: Any,
) → StatusCode
```

Type and source details:

- [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Set the state of an attribute.

Corresponds to viSetAttribute function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **attribute** (constants.ResourceAttribute) – Attribute for which the state is to be modified.

- **attribute_state** (Any) – The state of the attribute to be set for the specified object.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

