# Reading ASCII values
Context: PyVISA introduction-3; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](addresses-data-and-backends-index.md)

### Reading ASCII values

Suppose your oscilloscope, opened as `inst`, is set to return **ASCII** data for the `CURV?` command. Then you can query the values with:

```python
>>> values = inst.query_ascii_values('CURV?')

```

`values` will be `list` containing the values from the device.

Often a `list` is not the desired result; you may prefer another container type, for example a `numpy.array`. One option is to convert the returned data afterward:

```python
>>> import numpy as np
>>> values = np.array(inst.query_ascii_values('CURV?'))

```

At times, avoiding that temporary list is more efficient. In those cases, pass the wanted container type directly with the query:

```python
>>> values = inst.query_ascii_values('CURV?', container=np.array)

```

In `container`, you can have any callable/type that takes an iterable.

Note

For numpy.array or numpy.ndarray containers, PyVISA can call numpy routines and avoid an intermediate representation during conversion.

Some devices send ASCII data as hex or oct instead of decimal numbers, and others may return an array of strings. For those cases, provide a `converter`. For example, when the expected integers are hex:

```python
>>> values = inst.query_ascii_values('CURV?', converter='x')

```

`converter` may be one of the Python [string formatting codes](https://docs.python.org/3/library/string.html#formatspec), or a callable that accepts one argument when you need custom behavior. The default converter is `'f'`.

Finally, some devices separate returned values with an unusual delimiter. If, for example, the separator is `'$'`, make this call:

```python
>>> values = inst.query_ascii_values('CURV?', separator='$')

```

You may supply a function that receives a string and returns an iterable. The separator defaults to `','` (comma).

