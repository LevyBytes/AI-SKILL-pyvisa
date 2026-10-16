# pyvisa.highlevel.VisaLibraryBase.get_buffer_from_id
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
get_buffer_from_id(job_id: VISAJobID) → SupportsBytes | None
```

Type and source details:

- [SupportsBytes](https://docs.python.org/3/library/typing.html#typing.SupportsBytes)
- [None](https://docs.python.org/3/library/constants.html#None)

Retrieve the buffer associated with a job id created in read_asynchronously

Parameters:

**job_id** (VISAJobID) – Id of the job for which to retrieve the buffer.

Returns:

Buffer holding the data, or None when the job id is not linked to any job.

Return type:

Optional[SupportsBytes]

*static *get_debug_info() → [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)] | [Dict](https://docs.python.org/3/library/typing.html#typing.Dict)[[str](https://docs.python.org/3/library/stdtypes.html#str), [Any](https://docs.python.org/3/library/typing.html#typing.Any)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.get_debug_info)

Override to return an iterable of lines with the backend debug details.

