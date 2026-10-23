# pyvisa.highlevel.VisaLibraryBase.get_buffer_from_id

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def get_buffer_from_id(self, job_id: VISAJobID) -> Optional[SupportsBytes]:
        """Retrieve the buffer associated with a job id created in read_asynchronously

        Parameters
        ----------
        job_id : VISAJobID
            Id of the job for which to retrieve the buffer.

        Returns
        -------
        Optional[SupportsBytes]
            Data storage buffer, or None when the job id is not associated with
            any job.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
