# pyvisa.highlevel.VisaLibraryBase.lock

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def lock(
        self,
        session: VISASession,
        lock_type: constants.Lock,
        timeout: int,
        requested_key: Optional[str] = None,
    ) -> Tuple[str, StatusCode]:
        """Establishes an access mode to the specified resources.

        Corresponds to viLock function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        lock_type : constants.Lock
            Specifies the type of lock requested.
        timeout : int
            Absolute time period (in milliseconds) that a resource waits to get
            unlocked by the locking session before returning an error.
        requested_key : Optional[str], optional
            Lock key requested when using a shared lock. For an exclusive lock,
            pass None.

        Returns
        -------
        Optional[str]
            Key for sharing the lock with other sessions, or None when the lock
            is exclusive.
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
