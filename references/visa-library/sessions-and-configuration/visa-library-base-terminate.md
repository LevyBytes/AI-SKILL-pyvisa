# pyvisa.highlevel.VisaLibraryBase.terminate
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
terminate(
    session: VISASession,
    degree: None,
    job_id: VISAJobID,
) → StatusCode
```

Type and source details:

- [None](https://docs.python.org/3/library/constants.html#None)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Request a VISA session to terminate normal execution of an operation.

Corresponds to viTerminate function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **degree** (None) – Not used in this version of the VISA specification.

- **job_id** (VISAJobId) - Operation identifier. When a user supplies None as the job_id value to viTerminate(), the VISA implementation is expected to abort calls in the current process that are running on the specified vi. Calls stopped in that manner should return VI_ERROR_ABORT.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

