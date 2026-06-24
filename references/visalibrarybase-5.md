# Visalibrarybase (part 5)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

write_from_file(session: VISASession, filename: [str](https://docs.python.org/3/library/stdtypes.html#str), count: [int](https://docs.python.org/3/library/functions.html#int)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.write_from_file)

Take data from a file and write it out synchronously.

Corresponds to viWriteFromFile function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **filename** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Name of file from which data will be read.

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to be written.

Returns:

- int – Number of bytes actually transferred

- StatusCode – Return value of the library call.

  write_memory(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), data: [int](https://docs.python.org/3/library/functions.html#int), width: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)[8, 16, 32, 64] | DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.write_memory)

Write a value to the specified memory space and offset.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Specifies the address space.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) – Number of bits that should be read.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.
