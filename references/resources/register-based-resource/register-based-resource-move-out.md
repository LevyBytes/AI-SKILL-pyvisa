# pyvisa.resources.RegisterBasedResource.move_out
Context: PyVISA pyvisa.resources.RegisterBasedResource; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](register-based-resource.md)

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

Copy a local memory block into the specified address space and offset.

Corresponds to viMoveOut\* functions of the VISA library.

Parameters:

- **space** (constants.AddressSpace) – Address space into which move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Byte offset for the address or register being read.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Element count to transfer; each element uses the same data width as the source.

- **data** (Iterable[[int](https://docs.python.org/3/library/functions.html#int)]) – Data to write to bus.

- **width** (Union[Literal[8, 16, 32, 64], constants.DataWidth]) – Bits per element for the transfer.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), optional) – Use 64 bits for the offset regardless of platform. Defaults to False.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

