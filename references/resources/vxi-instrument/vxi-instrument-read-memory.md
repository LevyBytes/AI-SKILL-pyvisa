# pyvisa.resources.VXIInstrument.read_memory
Context: PyVISA pyvisa.resources.VXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-instrument.md)

```text
read_memory(
    space: AddressSpace,
    offset: int,
    width: DataWidth,
    extended: bool = False,
) → int
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [bool](https://docs.python.org/3/library/functions.html#bool)

Read a value from the specified memory space and offset.

Parameters:

- **space** (constants.AddressSpace) – Specifies the address space from which to read.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) - Byte offset of the address or register used as the read starting point.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Number of bits to read (8, 16, 32 or 64).

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits offset independent of the platform.

Returns:

**data** – Data read from memory

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

