# Visalibrarybase (part 3)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

**length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **data** (Iterable\*\*[[int](https://docs.python.org/3/library/functions.html#int)]) – Data to write to bus.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) – Number of bits used for each element.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

move_out_16(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), data: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[int](https://docs.python.org/3/library/functions.html#int)], extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move_out_16)

Moves an 16-bit block of data from local memory.

Corresponds to viMoveOut16\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space into which move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **data** (Iterable\*\*[[int](https://docs.python.org/3/library/functions.html#int)]) – Data to write to bus.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

move_out_32(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), data: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[int](https://docs.python.org/3/library/functions.html#int)], extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move_out_32)

Moves an 32-bit block of data from local memory.

Corresponds to viMoveOut32\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space into which move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **data** (Iterable\*\*[[int](https://docs.python.org/3/library/functions.html#int)]) – Data to write to bus.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

move_out_64(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), data: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[int](https://docs.python.org/3/library/functions.html#int)], extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move_out_64)

Moves an 64-bit block of data from local memory.

Corresponds to viMoveOut64\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space into which move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **data** (Iterable\*\*[[int](https://docs.python.org/3/library/functions.html#int)]) – Data to write to bus.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

move_out_8(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), data: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[int](https://docs.python.org/3/library/functions.html#int)], extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move_out_8)

Moves an 8-bit block of data from local memory.

Corresponds to viMoveOut8\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space into which move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **data** (Iterable\*\*[[int](https://docs.python.org/3/library/functions.html#int)]) – Data to write to bus.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

open(session: VISARMSession, resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str), access_mode: [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes) = AccessModes.no_lock, open_timeout: [int](https://docs.python.org/3/library/functions.html#int) = 0) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[VISASession, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.open)

Opens a session to the specified resource.

Corresponds to viOpen function of the VISA library.

Parameters:

- **session** (VISARMSession) – Resource Manager session (should always be a session returned from open_default_resource_manager()).

- **resource_name** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Unique symbolic name of a resource.

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), \*\*optional) – Specifies the mode by which the resource is to be accessed.

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int)) – If the `access_mode` parameter requests a lock, this value gives the absolute wait time (in milliseconds) before the operation returns an error while waiting for the resource to unlock.

Returns:

- VISASession – Unique logical identifier reference to a session

- StatusCode – Return value of the library call.

  open_default_resource_manager() → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[VISARMSession, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.open_default_resource_manager)

This function returns a session to the Default Resource Manager resource.

Corresponds to viOpenDefaultRM function of the VISA library.

Returns:

- VISARMSession – Unique logical identifier to a Default Resource Manager session

- StatusCode – Return value of the library call.

  out_16(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), data: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.out_16)

Write a 16-bit value to the specified memory space and offset.

Corresponds to viOut16\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space into which to write.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits offset independent of the platform.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

out_32(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), data: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[int](https://docs.python.org/3/library/functions.html#int)], extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.out_32)

Write a 32-bit value to the specified memory space and offset.

Corresponds to viOut32\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space into which to write.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits offset independent of the platform.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

out_64(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), data: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[int](https://docs.python.org/3/library/functions.html#int)], extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.out_64)

Write a 64-bit value to the specified memory space and offset.

Corresponds to viOut64\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space into which to write.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits offset independent of the platform.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

out_8(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), data: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.out_8)

Write an 8-bit value to the specified memory space and offset.

Corresponds to viOut8\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space into which to write.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits offset independent of the platform.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

parse_resource(session: VISARMSession, resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[ResourceInfo](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceInfo), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.parse_resource)

Parse a resource string to get the interface information.

Corresponds to viParseRsrc function of the VISA library.

Parameters:

- **session** (VISARMSession) – Resource Manager session, normally the Default Resource Manager for VISA returned from open_default_resource_manager().

- **resource_name** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Unique symbolic name of a resource.

Returns:

- ResourceInfo – Resource information with interface type and board number

- StatusCode – Return value of the library call.

  parse_resource_extended(session: VISARMSession, resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[ResourceInfo](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceInfo), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.parse_resource_extended)

Parse a resource string to get extended interface information.

Corresponds to viParseRsrcEx function of the VISA library.

Parameters:

- **session** (VISARMSession) – Resource Manager session, normally the Default Resource Manager for VISA returned from open_default_resource_manager().

- **resource_name** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Unique symbolic name of a resource.

Returns:

- ResourceInfo – Resource information with interface type and board number

- StatusCode – Return value of the library call.

  peek(session: VISASession, address: VISAMemoryAddress, width: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)[8, 16, 32, 64] | DataWidth) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.peek)

Reads a value of 8, 16, 32, or 64-bit width from the specified address.

Corresponds to viPeek\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) – Number of bits that should be read.

Returns:

- **data** (int) – Data read from bus

- **status_code** (StatusCode) – Return value of the library call.

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

peek_16(session: VISASession, address: VISAMemoryAddress) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.peek_16)

Read an 16-bit value from the specified address.

Corresponds to viPeek16 function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

Returns:

- int – Data read from bus

- StatusCode – Return value of the library call.

  peek_32(session: VISASession, address: VISAMemoryAddress) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.peek_32)

Read an 32-bit value from the specified address.

Corresponds to viPeek32 function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

Returns:

- int – Data read from bus

- StatusCode – Return value of the library call.

  peek_64(session: VISASession, address: VISAMemoryAddress) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.peek_64)

Read an 64-bit value from the specified address.

Corresponds to viPeek64 function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

Returns:

- int – Data read from bus

- StatusCode – Return value of the library call.

  peek_8(session: VISASession, address: VISAMemoryAddress) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.peek_8)

Read an 8-bit value from the specified address.

Corresponds to viPeek8 function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

Returns:

- int – Data read from bus

- StatusCode – Return value of the library call.

  poke(session: VISASession, address: VISAMemoryAddress, width: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)[8, 16, 32, 64] | DataWidth, data: [int](https://docs.python.org/3/library/functions.html#int)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.poke)

Writes a value of 8, 16, 32, or 64-bit width from the specified address.

Corresponds to viPoke\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) – Number of bits that should be read.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to the bus

Returns:

**status_code** – Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

poke_16(session: VISASession, address: VISAMemoryAddress, data: [int](https://docs.python.org/3/library/functions.html#int)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.poke_16)

Write an 16-bit value to the specified address.

Corresponds to viPoke16 function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

poke_32(session: VISASession, address: VISAMemoryAddress, data: [int](https://docs.python.org/3/library/functions.html#int)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.poke_32)

Write an 32-bit value to the specified address.

Corresponds to viPoke32 function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

-
