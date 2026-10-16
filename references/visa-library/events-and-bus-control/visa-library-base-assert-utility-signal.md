# pyvisa.highlevel.VisaLibraryBase.assert_utility_signal
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
assert_utility_signal(session: VISASession, line: UtilityBusSignal) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Assert or deassert the specified utility bus signal.

Corresponds to viAssertUtilSignal function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **line** (constants.UtilityBusSignal) – Specifies the utility bus signal to assert.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

