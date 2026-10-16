# pyvisa.highlevel.VisaLibraryBase.parse_resource
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
parse_resource(session: VISARMSession, resource_name: str) → Tuple[ResourceInfo, StatusCode]
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [ResourceInfo](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceInfo)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Parse a resource string to get the interface information.

Corresponds to viParseRsrc function of the VISA library.

Parameters:

- **session** (VISARMSession) – Resource Manager session, normally the Default Resource Manager for VISA returned from open_default_resource_manager().

- **resource_name** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Unique symbolic name of a resource.

Returns:

- ResourceInfo – Resource information with interface type and board number

- StatusCode – Return value of the library call.

