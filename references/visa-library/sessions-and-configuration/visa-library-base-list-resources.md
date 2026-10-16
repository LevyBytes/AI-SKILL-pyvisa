# pyvisa.highlevel.VisaLibraryBase.list_resources
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
list_resources(session: VISARMSession, query: str = '?*::INSTR') → Tuple[str, ...]
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)

Return a tuple of all connected devices matching query.

Parameters:

- **session** (VISARMSession) – Unique logical identifier to the resource manager session.

- **query** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Regular expression used to match devices.

Returns:

Resource names of all the connected devices matching the query.

Return type:

Tuple[[str](https://docs.python.org/3/library/stdtypes.html#str), …]

