# pyvisa.resources.TCPIPInstrument.chunk_size
Context: PyVISA pyvisa.resources.TCPIPInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](tcpip-instrument.md)

```text
chunk_size: int = 20480
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)

Bytes requested per read chunk. Some resources, such as serial resources, may reject large chunk sizes.

