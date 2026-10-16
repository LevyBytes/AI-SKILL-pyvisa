# Writing ASCII values
Context: PyVISA introduction-3; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](addresses-data-and-backends-index.md)

### Writing ASCII values

For an arbitrary wave generator, uploading a function shape might use `WLISt:WAVeform:DATA <waveform name>,<function data>`; `<waveform name>` is the storage name on the device.

```python
>>> values = list(range(100))
>>> inst.write_ascii_values('WLISt:WAVeform:DATA somename,', values)

```

Again, you can specify the converter code.

```python
>>> inst.write_ascii_values('WLISt:WAVeform:DATA somename,', values, converter='x')

```

`converter` accepts any Python [string formatting codes](https://docs.python.org/3/library/string.html#formatspec), or, when necessary, a callable that receives one argument. Its default value is `'f'`.

The separator can also be specified just like in `query_ascii_values`.

```python
>>> inst.write_ascii_values('WLISt:WAVeform:DATA somename,', values, converter='x', separator='$')

```

You may supply a function that receives an iterable and returns a string. The separator defaults to `','` (comma).

