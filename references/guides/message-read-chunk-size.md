# Chunk length
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

### Attributes of MessageBase resources

### Chunk length

When data is read from a device, PyVISA needs a buffer before the transfer begins. Because the library has to allocate storage ahead of the read, it must estimate how many bytes the device will provide, and that amount is not known a priori.

PyVISA therefore performs reads in chunks. The default chunk size is 20 kilobytes. If unread data remains, PyVISA repeats the read loop, combines the collected pieces, and gives the result back. That 20 kilobytes default is large enough that many transfers finish in a single cycle.

This process is automatic, so it usually requires no attention. Some instruments, however, do not behave well with chunked transfers. If a specific device fails and you expect responses longer than the default chunk length, increase the chunk size, for example with:

```python
my_instrument.chunk_size = 102400

```

This example sets it to 100 kilobytes.

