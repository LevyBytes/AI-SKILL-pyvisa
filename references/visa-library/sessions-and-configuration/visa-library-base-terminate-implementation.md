# pyvisa.highlevel.VisaLibraryBase.terminate

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def terminate(
        self, session: VISASession, degree: None, job_id: VISAJobID
    ) -> StatusCode:
        """Request a VISA session to terminate normal execution of an operation.

        Corresponds to viTerminate function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        degree : None
            Not used in this version of the VISA specification.
        job_id : VISAJobId
            Specifies an operation identifier. If a user passes None as the
            job_id value to viTerminate(), a VISA implementation should abort
            any calls in the current process executing on the specified vi.
            Any call that is terminated this way should return VI_ERROR_ABORT.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
