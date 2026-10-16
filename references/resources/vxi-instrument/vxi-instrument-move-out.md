# pyvisa.resources.VXIInstrument.move_out
Context: PyVISA pyvisa.resources.VXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](vxi-instrument.md)

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

Transfer a data block from local memory into the specified address space and offset.

Corresponds to viMoveOut\* functions of the VISA library.

Parameters:

- **space** (constants.AddressSpace) – Address space into which move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) - Address or register byte offset used as the read starting point.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) - Element count for the transfer; each element uses the same data width as the source data width.

- **data** (Iterable[[int](https://docs.python.org/3/library/functions.html#int)]) – Data to write to bus.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) - Bits used for each element.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) - Use an offset of 64 bits regardless of platform; default is False.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

