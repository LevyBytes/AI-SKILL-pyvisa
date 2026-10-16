# pyvisa.highlevel.VisaLibraryBase.flush
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
flush(session: VISASession, mask: BufferOperation) → StatusCode
```

Type and source details:

- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Flush the specified buffers.

These buffers may belong to formatted I/O operations, serial communication, or both.

Corresponds to viFlush function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mask** (constants.BufferOperation) – Specifies which buffer-flush action to perform. The values can be combined using the | operator, but multiple operations targeting one buffer cannot be combined.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

