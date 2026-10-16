# Writing binary values
Context: PyVISA introduction-3; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](addresses-data-and-backends-index.md)

### Writing binary values

A binary upload of a function shape to an arbitrary wave generator can use a command such as `WLISt:WAVeform:DATA <waveform name>,<function data>`; the device stores the data under `<waveform name>`.

```python
>>> values = list(range(100))
>>> inst.write_binary_values('WLISt:WAVeform:DATA somename,', values)

```

Again you can specify the `datatype` and `endianness`.

```python
>>> inst.write_binary_values('WLISt:WAVeform:DATA somename,', values, datatype='d', is_big_endian=False)

```

For data already stored in a `bytes` object, use the `"s"` format.

