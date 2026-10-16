# pyvisa.highlevel.VisaLibraryBase.lock
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
lock(
    session: VISASession,
    lock_type: Lock,
    timeout: int,
    requested_key: str | None = None,
) → Tuple[str, StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [None](https://docs.python.org/3/library/constants.html#None)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Establishes an access mode to the specified resources.

Corresponds to viLock function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **lock_type** (constants.Lock) – Specifies the type of lock requested.

- **timeout** ([int](https://docs.python.org/3/library/functions.html#int)) – Absolute timeout (in milliseconds) that a resource waits for the locking session to release it before returning an error.

- **requested_key** (Optional[[str](https://docs.python.org/3/library/stdtypes.html#str)], optional) – Requested locking key for a shared lock. For an exclusive lock, it should be None.

Returns:

- Optional[str] – Key that other sessions can use to share the lock, or None for an exclusive lock.

- StatusCode – Return value of the library call.

