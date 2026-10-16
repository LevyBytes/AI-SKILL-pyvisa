# query_delay and send_end
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

### query_delay and send_end

There are two further options related to message termination, namely `send_end` and `query_delay`.

`send_end` is a boolean. With the default value, `True`, PyVISA asserts the EOI line after each write to mark completion. EOI is specific to GPIB, although PyVISA applies comparable behavior for other interfaces.

`query_delay` gives the wait time, in seconds, inserted after each write while running a query. For example:

```python
my_instrument = rm.open_resource("GPIB::10", send_end=False, query_delay=1.2)

```

This configuration uses a 1.2 seconds delay and skips asserting the EOI line. Skipping EOI is not recommended; if you choose that setting anyway, make sure the device protocol calls for it.

