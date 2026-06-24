# Visalibrarybase (part 2)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

**extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; False by default.

Returns:

- int – Data read from memory

- StatusCode – Return value of the library call.

  install_handler(session: VISASession, event_type: EventType, handler: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)], user_handle: [Any](https://docs.python.org/3/library/typing.html#typing.Any)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)], [Any](https://docs.python.org/3/library/typing.html#typing.Any), [Any](https://docs.python.org/3/library/typing.html#typing.Any), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.install_handler)

Install handlers for event callbacks.

Corresponds to viInstallHandler function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **event_type** (constants.EventType) – Logical event identifier.

- **handler** (VISAHandler) – Reference to a handler that a client application installs.

- **user_handle** (Any) – Application-supplied value used to identify handlers uniquely for one event type.

Returns:

- **handler** (VISAHandler) – Handler to be installed by a client application.

- converted_user_handle – User handle converted to match the underlying library. Use this handle form for later calls to the library.

- converted_handler – Converted version of the handler satisfying to backend library.

- **status_code** (StatusCode) – Return value of the library call

  install_visa_handler(session: VISASession, event_type: EventType, handler: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)], user_handle: [Any](https://docs.python.org/3/library/typing.html#typing.Any) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [Any](https://docs.python.org/3/library/typing.html#typing.Any)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.install_visa_handler)

Installs handlers for event callbacks.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **event_type** (constants.EventType\*\*,\_) – Logical event identifier.

- **handler** (VISAHandler) – Handler to be installed by a client application.

- **user_handle** – Application-supplied value used to identify handlers uniquely for one event type.

Returns:

User handle converted to match the underlying library. Use this handle form for later calls to the library.

Return type:

converted_user_handle

issue_warning_on*: [Set](https://docs.python.org/3/library/typing.html#typing.Set)[[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)]*

Set error codes on which to issue a warning.

*property *last_status*: [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)*

Last return value of the library.

library_path*: LibraryPath*

Path to the VISA library used by this instance

list_resources(session: VISARMSession, query: [str](https://docs.python.org/3/library/stdtypes.html#str) = '?\*::INSTR') → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[str](https://docs.python.org/3/library/stdtypes.html#str), ...][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.list_resources)

Return a tuple of all connected devices matching query.

Parameters:

- **session** (VISARMSession) – Unique logical identifier to the resource manager session.

- **query** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Regular expression used to match devices.

Returns:

Resource names of all the connected devices matching the query.

Return type:

Tuple[[str](https://docs.python.org/3/library/stdtypes.html#str), …]

lock(session: VISASession, lock_type: Lock, timeout: [int](https://docs.python.org/3/library/functions.html#int), requested_key: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[str](https://docs.python.org/3/library/stdtypes.html#str), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.lock)

Establishes an access mode to the specified resources.

Corresponds to viLock function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **lock_type** (constants.Lock) – Specifies the type of lock requested.

- **timeout** ([int](https://docs.python.org/3/library/functions.html#int)) – Absolute timeout (in milliseconds) that a resource waits for the locking session to release it before returning an error.

- **requested_key** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Requested locking key for a shared lock. For an exclusive lock, it should be None.

Returns:

- Optional[str] – Key that other sessions can use to share the lock, or None for an exclusive lock.

- StatusCode – Return value of the library call.

  map_address(session: VISASession, map_space: AddressSpace, map_base: [int](https://docs.python.org/3/library/functions.html#int), map_size: [int](https://docs.python.org/3/library/functions.html#int), access: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)[False] = False, suggested: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.map_address)

Maps the specified memory space into the process’s address space.

Corresponds to viMapAddress function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **map_space** (constants.AddressSpace) – Specifies the address space to map.

- **map_base** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) of the memory to be mapped.

- **map_size** ([int](https://docs.python.org/3/library/functions.html#int)) – Amount of memory to map (in bytes).

- **access** (False) – Unused parameter.

- **suggested** (Optional\*\*[[int](https://docs.python.org/3/library/functions.html#int)]**, **optional) – If not None, the operating system attempts to map memory at the specified address. That address is not guaranteed; this operation may instead place the mapping in a different address region than the suggested one.

Returns:

- int – Address in your process space where the memory was mapped

- StatusCode – Return value of the library call.

  map_trigger(session: VISASession, trigger_source: InputTriggerLine, trigger_destination: OutputTriggerLine, mode: [None](https://docs.python.org/3/library/constants.html#None) = None) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.map_trigger)

Map the specified trigger source line to the specified destination line.

Corresponds to viMapTrigger function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **trigger_source** (constants.InputTriggerLine) – Source line from which to map.

- **trigger_destination** (constants.OutputTriggerLine) – Destination line to which to map.

- **mode** (None**, **optional) – Always None for this version of the VISA specification.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

memory_allocation(session: VISASession, size: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.memory_allocation)

Allocate memory from a resource’s memory region.

Corresponds to viMemAlloc\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **size** ([int](https://docs.python.org/3/library/functions.html#int)) – Specifies the size of the allocation.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits offset independent of the platform.

Returns:

- int – offset of the allocated memory

- StatusCode – Return value of the library call.

  memory_free(session: VISASession, offset: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.memory_free)

Frees memory previously allocated using the memory_allocation() operation.

Corresponds to viMemFree\* function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset of the memory to free.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits offset independent of the platform.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

move(session: VISASession, source_space: AddressSpace, source_offset: [int](https://docs.python.org/3/library/functions.html#int), source_width: DataWidth, destination_space: AddressSpace, destination_offset: [int](https://docs.python.org/3/library/functions.html#int), destination_width: DataWidth, length: [int](https://docs.python.org/3/library/functions.html#int)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move)

Moves a block of data.

Corresponds to viMove function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **source_space** (constants.AddressSpace) – Specifies the address space of the source.

- **source_offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset of the starting address or register from which to read.

- **source_width** (constants.DataWidth) – Specifies the data width of the source.

- **destination_space** (constants.AddressSpace) – Specifies the address space of the destination.

- **destination_offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset of the starting address or register to which to write.

- **destination_width** (constants.DataWidth) – Specifies the data width of the destination.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

move_asynchronously(session: VISASession, source_space: AddressSpace, source_offset: [int](https://docs.python.org/3/library/functions.html#int), source_width: DataWidth, destination_space: AddressSpace, destination_offset: [int](https://docs.python.org/3/library/functions.html#int), destination_width: DataWidth, length: [int](https://docs.python.org/3/library/functions.html#int)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[VISAJobID, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move_asynchronously)

Moves a block of data asynchronously.

Corresponds to viMoveAsync function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **source_space** (constants.AddressSpace) – Specifies the address space of the source.

- **source_offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset of the starting address or register from which to read.

- **source_width** (constants.DataWidth) – Specifies the data width of the source.

- **destination_space** (constants.AddressSpace) – Specifies the address space of the destination.

- **destination_offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset of the starting address or register to which to write.

- **destination_width** (constants.DataWidth) – Specifies the data width of the destination.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

Returns:

- VISAJobID – Job identifier of this asynchronous move operation

- StatusCode – Return value of the library call.

  `move_in`(session: `VISASession`_, space: `AddressSpace`_, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), width: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)[8, 16, 32, 64] | `DataWidth`\_, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[List](https://docs.python.org/3/library/typing.html#typing.List)[[int](https://docs.python.org/3/library/functions.html#int)], [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move_in)

Moves a data block from the given address space and offset into local memory.

Corresponds to viMoveIn\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space from which to move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) - Bit width applied when reading each individual element.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (StatusCode) – Return value of the library call.

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

move_in_16(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[List](https://docs.python.org/3/library/typing.html#typing.List)[[int](https://docs.python.org/3/library/functions.html#int)], [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move_in_16)

Moves an 16-bit block of data to local memory.

Corresponds to viMoveIn816 functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space from which to move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (StatusCode) – Return value of the library call.

  move_in_32(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[List](https://docs.python.org/3/library/typing.html#typing.List)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move_in_32)

Moves an 32-bit block of data to local memory.

Corresponds to viMoveIn32\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space from which to move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (StatusCode) – Return value of the library call.

  move_in_64(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[List](https://docs.python.org/3/library/typing.html#typing.List)[[int](https://docs.python.org/3/library/functions.html#int)], [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move_in_64)

Moves an 64-bit block of data to local memory.

Corresponds to viMoveIn8\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space from which to move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (StatusCode) – Return value of the library call.

  move_in_8(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[List](https://docs.python.org/3/library/typing.html#typing.List)[[int](https://docs.python.org/3/library/functions.html#int)], [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move_in_8)

Moves an 8-bit block of data to local memory.

Corresponds to viMoveIn8\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space from which to move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of elements to transfer; each element uses the same data width as the source.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; by default False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (StatusCode) – Return value of the library call.

  move_out(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), data: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[int](https://docs.python.org/3/library/functions.html#int)], width: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)[8, 16, 32, 64] | DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.move_out)

Moves a data block from local memory to the specified address space and offset.

Corresponds to viMoveOut\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Address space into which move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

-
