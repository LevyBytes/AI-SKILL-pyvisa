# When things are not what they should be
Context: PyVISA introduction-3; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](addresses-data-and-backends-index.md)

### When things are not what they should be

PyVISA makes transfers to and from a device straightforward. The methods above handle 99% of situations, but a device can still ignore standard protocols so completely that none of the arguments described earlier can adapt to it.

In those cases, you need to get the data:

```python
>>> inst.write('CURV?')
>>> data = inst.read_raw()

```

and then you need to implement the logic to parse it.

If the read_raw call fails instead, try reading only a small number of bytes with:

```python
>>> inst.write('CURV?')
>>> data = inst.read_bytes(1)

```

A failure here can mean the instrument did not respond because it needs additional time, or because the first instruction was not understood.

