# pyvisa.resources.FirewireInstrument.move_out
Context: PyVISA pyvisa.resources.FirewireInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](firewire-instrument.md)

```text
move_out(
    space: AddressSpace,
    offset: int,
    length: int,
    data: Iterable[int],
    width: DataWidth,
    extended: bool = False,
) → StatusCode
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)
- [bool](https://docs.python.org/3/library/functions.html#bool)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Move a data block from local memory to the given address space and offset.

This maps to the VISA library viMoveOut\* functions.

Parameters:

- **space** (constants.AddressSpace) – Address space into which data is moved.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset, in bytes, for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **data** (Iterable[[int](https://docs.python.org/3/library/functions.html#int)]) – Data to write to the bus.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Bit count for each element.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use a 64 bits offset regardless of platform. Defaults to False.

Returns:

Status returned by the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised when width is invalid.

