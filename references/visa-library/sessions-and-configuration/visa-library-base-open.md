# pyvisa.highlevel.VisaLibraryBase.open
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
open(
    session: VISARMSession,
    resource_name: str,
    access_mode: AccessModes = AccessModes.no_lock,
    open_timeout: int = 0,
) → Tuple[VISASession, StatusCode]
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes)
- [int](https://docs.python.org/3/library/functions.html#int)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [VISASession, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Opens a session to the specified resource.

Corresponds to viOpen function of the VISA library.

Parameters:

- **session** (VISARMSession) – Resource Manager session (should always be a session returned from open_default_resource_manager()).

- **resource_name** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Unique symbolic name of a resource.

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), optional) – Specifies the mode by which the resource is to be accessed.

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int)) – If the `access_mode` parameter requests a lock, this value gives the absolute wait time (in milliseconds) before the operation returns an error while waiting for the resource to unlock.

Returns:

- VISASession – Unique logical identifier reference to a session

- StatusCode – Return value of the library call.

