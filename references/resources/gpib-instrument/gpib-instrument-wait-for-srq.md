# pyvisa.resources.GPIBInstrument.wait_for_srq
Context: PyVISA pyvisa.resources.GPIBInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-instrument.md)

```text
wait_for_srq(timeout: int = 25000) → None
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [None](https://docs.python.org/3/library/constants.html#None)

Wait for a Service Request (SRQ) coming from the instrument.

This method only ends for an SRQ from this instrument, not from another instrument.

Parameters:

**timeout** ([int](https://docs.python.org/3/library/functions.html#int)) – Maximum wait in milliseconds. Defaul: 25000 (milliseconds). None waits forever if necessary.

