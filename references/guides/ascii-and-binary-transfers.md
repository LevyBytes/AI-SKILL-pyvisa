# Reading and Writing values
Context: PyVISA introduction-3; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](addresses-data-and-backends-index.md)

## Reading and Writing values

### Reading and Writing values

Some instruments can exchange large datasets with the computer using one query. For instance, an oscilloscope may return an entire voltage trace, while an arbitrary wave generator may require you to send the function it should generate.

These transfers usually use either ASCII form, which is slower but easy to read, or binary form, which is faster but harder to inspect during debugging.

PyVISA Message Based Resources have different methods for this called [`read_ascii_values()`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.read_ascii_values), [`query_ascii_values()`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.query_ascii_values) and [`read_binary_values()`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.read_binary_values), [`query_binary_values()`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.query_binary_values).

