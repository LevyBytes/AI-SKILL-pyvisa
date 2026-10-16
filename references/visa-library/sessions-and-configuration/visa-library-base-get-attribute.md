# pyvisa.highlevel.VisaLibraryBase.get_attribute
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
get_attribute(session: VISASession | VISAEventContext | VISARMSession, attribute: ResourceAttribute | EventAttribute) → Tuple[Any, StatusCode]
```

Type and source details:

- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [Any](https://docs.python.org/3/library/typing.html#typing.Any)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Retrieves the state of an attribute.

Corresponds to viGetAttribute function of the VISA library.

Parameters:

- **session** (Union[VISASession, VISAEventContext]) – Unique logical identifier for a session, event, or find list.

- **attribute** (Union[constants.ResourceAttribute, constants.EventAttribute]) – Resource or event attribute whose current state is requested.

Returns:

- Any – State of the queried attribute for a specified resource

- StatusCode – Return value of the library call.

