# pyvisa.highlevel.VisaLibraryBase.gpib_pass_control
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
gpib_pass_control(
    session: VISASession,
    primary_address: int,
    secondary_address: int,
) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Tell a GPIB device to become controller in charge (CIC).

Corresponds to viGpibPassControl function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **primary_address** ([int](https://docs.python.org/3/library/functions.html#int)) – Primary address of the GPIB device to which you want to pass control.

- **secondary_address** ([int](https://docs.python.org/3/library/functions.html#int)) – Secondary address for the targeted GPIB device. If that device has no secondary address, this parameter should contain the value Constants.VI_NO_SEC_ADDR.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

