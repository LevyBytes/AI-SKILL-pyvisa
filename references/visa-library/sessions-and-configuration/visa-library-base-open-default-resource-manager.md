# pyvisa.highlevel.VisaLibraryBase.open_default_resource_manager
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
open_default_resource_manager() → Tuple[VISARMSession, StatusCode]
```

Type and source details:

- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [VISARMSession, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

This function returns a session to the Default Resource Manager resource.

Corresponds to viOpenDefaultRM function of the VISA library.

Returns:

- VISARMSession – Unique logical identifier to a Default Resource Manager session

- StatusCode – Return value of the library call.

