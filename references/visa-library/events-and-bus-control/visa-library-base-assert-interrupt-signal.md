# pyvisa.highlevel.VisaLibraryBase.assert_interrupt_signal
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
assert_interrupt_signal(
    session: VISASession,
    mode: AssertSignalInterrupt,
    status_id: int,
) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Asserts the specified interrupt or signal.

Corresponds to viAssertIntrSignal function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mode** (constants.AssertSignalInterrupt) – How to assert the interrupt.

- **status_id** ([int](https://docs.python.org/3/library/functions.html#int)) – Status value to be presented during an interrupt acknowledge cycle.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

