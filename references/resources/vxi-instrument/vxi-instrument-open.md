# pyvisa.resources.VXIInstrument.open
Context: PyVISA pyvisa.resources.VXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-instrument.md)

```text
open(access_mode: AccessModes = AccessModes.no_lock, open_timeout: int = 5000) → None
```

Type and source details:

- [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes)
- [int](https://docs.python.org/3/library/functions.html#int)
- [None](https://docs.python.org/3/library/constants.html#None)

Opens a session to the specified resource.

Parameters:

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), optional) - Access mode used for opening the resource. Defaults to constants.AccessModes.no_lock.

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int), optional) - When `access_mode` asks for a lock, this is the absolute wait time, in milliseconds, for the resource to become unlocked before an error is returned. Defaults to 5000.

