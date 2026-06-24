# Visalibrarybase (part 4)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

**data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

poke_64(session: VISASession, address: VISAMemoryAddress, data: [int](https://docs.python.org/3/library/functions.html#int)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.poke_64)

Write an 64-bit value to the specified address.

Corresponds to viPoke64 function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

poke_8(session: VISASession, address: VISAMemoryAddress, data: [int](https://docs.python.org/3/library/functions.html#int)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.poke_8)

Write an 8-bit value to the specified address.

Corresponds to viPoke8 function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **address** (VISAMemoryAddress) – Source address to read the value.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

read(session: VISASession, count: [int](https://docs.python.org/3/library/functions.html#int)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[bytes](https://docs.python.org/3/library/stdtypes.html#bytes), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.read)

Reads data from device or interface synchronously.

Corresponds to viRead function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to be read.

Returns:

- bytes – Date read

- StatusCode – Return value of the library call.

  read_asynchronously(session: VISASession, count: [int](https://docs.python.org/3/library/functions.html#int)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[SupportsBytes](https://docs.python.org/3/library/typing.html#typing.SupportsBytes), VISAJobID, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.read_asynchronously)

Reads data from device or interface asynchronously.

Corresponds to viReadAsync function of the VISA library. Because the asynchronous operation may finish before the function call returns, implementations should make sure get_buffer_from_id can provide the proper buffer before this method returns.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to be read.

Returns:

- SupportsBytes – Buffer that will be filled during the asynchronous operation.

- VISAJobID – Id of the asynchronous job

- StatusCode – Return value of the library call.

  read_memory(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), width: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)[8, 16, 32, 64] | DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.read_memory)

Read a value from the specified memory space and offset.

Corresponds to viIn\* functions of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Specifies the address space from which to read.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) – Number of bits to read (8, 16, 32 or 64).

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits offset independent of the platform.

Returns:

- **data** (int) – Data read from memory

- **status_code** (StatusCode) – Return value of the library call.

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

read_stb(session: VISASession) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.read_stb)

Reads a status byte of the service request.

Corresponds to viReadSTB function of the VISA library.

Parameters:

**session** (VISASession) – Unique logical identifier to a session.

Returns:

- int – Service request status byte

- StatusCode – Return value of the library call.

  read_to_file(session: VISASession, filename: [str](https://docs.python.org/3/library/stdtypes.html#str), count: [int](https://docs.python.org/3/library/functions.html#int)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.read_to_file)

Read data synchronously, and store the transferred data in a file.

Corresponds to viReadToFile function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **filename** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Name of file to which data will be written.

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to be read.

Returns:

- int – Number of bytes actually transferred

- StatusCode – Return value of the library call.

  resource_manager*: [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) | [None](https://docs.python.org/3/library/constants.html#None)*

Default ResourceManager instance for this library.

set_attribute(session: VISASession, attribute: ResourceAttribute, attribute_state: [Any](https://docs.python.org/3/library/typing.html#typing.Any)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.set_attribute)

Set the state of an attribute.

Corresponds to viSetAttribute function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **attribute** (constants.ResourceAttribute) – Attribute for which the state is to be modified.

- **attribute_state** (Any) – The state of the attribute to be set for the specified object.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

set_buffer(session: VISASession, mask: BufferType, size: [int](https://docs.python.org/3/library/functions.html#int)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.set_buffer)

Sets the size of the formatted I/O buffer(s), low-level I/O communication buffer(s), or both.

Corresponds to viSetBuf function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mask** (constants.BufferType) – Specifies the type of buffer.

- **size** ([int](https://docs.python.org/3/library/functions.html#int)) – The size to be set for the specified buffer(s).

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

status_description(session: VISASession, status: [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[str](https://docs.python.org/3/library/stdtypes.html#str), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.status_description)

Returns a user-readable description for the status code supplied to the operation.

Corresponds to viStatusDesc function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **status** ([StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)) – Status code to interpret.

Returns:

- str – User-readable string interpretation of the status code.

- StatusCode – Return value of the library call.

  terminate(session: VISASession, degree: [None](https://docs.python.org/3/library/constants.html#None), job_id: VISAJobID) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.terminate)

Request a VISA session to terminate normal execution of an operation.

Corresponds to viTerminate function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **degree** (None) – Not used in this version of the VISA specification.

- **job_id** (VISAJobId) - Operation identifier. When a user supplies None as the job_id value to viTerminate(), the VISA implementation is expected to abort calls in the current process that are running on the specified vi. Calls stopped in that manner should return VI_ERROR_ABORT.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

uninstall_all_visa_handlers(session: VISASession | [None](https://docs.python.org/3/library/constants.html#None)) → [None](https://docs.python.org/3/library/constants.html#None)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.uninstall_all_visa_handlers)

Uninstalls all previously installed handlers for a particular session.

Parameters:

**session** (VISASession** | **None) – Unique logical identifier for a session. If None, operates across all sessions.

uninstall_handler(session: VISASession, event_type: EventType, handler: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)], user_handle: [Any](https://docs.python.org/3/library/typing.html#typing.Any) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.uninstall_handler)

Uninstall handlers for events.

Corresponds to viUninstallHandler function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **event_type** (constants.EventType) – Logical event identifier.

- **handler** (VISAHandler) – Handler to be uninstalled by a client application.

- **user_handle** – Application-supplied value used to identify handlers uniquely for an event within a session. Use the modified user_handle returned by install_handler instead of the original value.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

uninstall_visa_handler(session: VISASession, event_type: EventType, handler: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)], user_handle: [Any](https://docs.python.org/3/library/typing.html#typing.Any) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [None](https://docs.python.org/3/library/constants.html#None)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.uninstall_visa_handler)

Uninstalls handlers for events.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **event_type** (constants.EventType) – Logical event identifier.

- **handler** (VISAHandler) – Handler to be uninstalled by a client application.

- **user_handle** – The user handle returned by install_visa_handler.

  unlock(session: VISASession) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.unlock)

Relinquish a lock for the specified resource.

Corresponds to viUnlock function of the VISA library.

Parameters:

**session** (VISASession) – Unique logical identifier to a session.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

unmap_address(session: VISASession) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.unmap_address)

Unmap memory space previously mapped by map_address().

Corresponds to viUnmapAddress function of the VISA library.

Parameters:

**session** (VISASession) – Unique logical identifier to a session.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

unmap_trigger(session: VISASession, trigger_source: InputTriggerLine, trigger_destination: OutputTriggerLine) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.unmap_trigger)

Reverses an existing mapping between a trigger source line and a destination line.

Corresponds to viUnmapTrigger function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **trigger_source** (constants.InputTriggerLine) – Source line used in previous map.

- **trigger_destination** (constants.OutputTriggerLine) – Destination line used in previous map.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

usb_control_in(session: VISASession, request_type_bitmap_field: [int](https://docs.python.org/3/library/functions.html#int), request_id: [int](https://docs.python.org/3/library/functions.html#int), request_value: [int](https://docs.python.org/3/library/functions.html#int), index: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int) = 0) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[bytes](https://docs.python.org/3/library/stdtypes.html#bytes), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.usb_control_in)

Perform a USB control pipe transfer from the device.

Corresponds to viUsbControlIn function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **request_type_bitmap_field** ([int](https://docs.python.org/3/library/functions.html#int)) – bmRequestType parameter of the setup stage of a USB control transfer.

- **request_id** ([int](https://docs.python.org/3/library/functions.html#int)) – bRequest parameter of the setup stage of a USB control transfer.

- **request_value** ([int](https://docs.python.org/3/library/functions.html#int)) – wValue parameter of the setup stage of a USB control transfer.

- **index** ([int](https://docs.python.org/3/library/functions.html#int)) – wIndex parameter for the setup stage of a USB control transfer. Usually identifies the interface or endpoint index.

- **length** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – wLength parameter for the setup stage of a USB control transfer. This value also gives the size of the data buffer used to receive data from the optional data stage of the control transfer.

Returns:

- bytes – Buffer populated by the optional data stage of the control transfer

- StatusCode – Return value of the library call.

  usb*control_out(session: VISASession, request_type_bitmap_field: [int](https://docs.python.org/3/library/functions.html#int), request_id: [int](https://docs.python.org/3/library/functions.html#int), request_value: [int](https://docs.python.org/3/library/functions.html#int), index: [int](https://docs.python.org/3/library/functions.html#int), data: [bytes](https://docs.python.org/3/library/stdtypes.html#bytes) = b''*) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.usb_control_out)

Perform a USB control pipe transfer to the device.

Corresponds to viUsbControlOut function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **request_type_bitmap_field** ([int](https://docs.python.org/3/library/functions.html#int)) – bmRequestType parameter of the setup stage of a USB control transfer.

- **request_id** ([int](https://docs.python.org/3/library/functions.html#int)) – bRequest parameter of the setup stage of a USB control transfer.

- **request_value** ([int](https://docs.python.org/3/library/functions.html#int)) – wValue parameter of the setup stage of a USB control transfer.

- **index** ([int](https://docs.python.org/3/library/functions.html#int)) – wIndex parameter for the setup stage of a USB control transfer. Usually identifies the interface or endpoint index.

- **data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes), \*\*optional) – Data buffer sent during the optional data stage of the control transfer.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

vxi_command_query(session: VISASession, mode: VXICommands, command: [int](https://docs.python.org/3/library/functions.html#int)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.vxi_command_query)

Sends a miscellaneous command or query to the device and/or retrieves an earlier query response.

Corresponds to viVxiCommandQuery function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mode** (constants.VXICommands) – Specifies whether to issue a command, retrieve a response, or both.

- **command** ([int](https://docs.python.org/3/library/functions.html#int)) – The miscellaneous command to send.

Returns:

- int – The response retrieved from the device

- StatusCode – Return value of the library call.

  wait_on_event(session: VISASession, in_event_type: EventType, timeout: [int](https://docs.python.org/3/library/functions.html#int)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[EventType, VISAEventContext, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.wait_on_event)

Wait for an occurrence of the specified event for a given session.

Corresponds to viWaitOnEvent function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **in_event_type** (constants.EventType) – Logical identifier of the event(s) to wait for.

- **timeout** ([int](https://docs.python.org/3/library/functions.html#int)) – Absolute wait time, in milliseconds, for the specified event before returning the time elapsed error.

Returns:

- constants.EventType – Logical identifier of the event actually received

- VISAEventContext – A handle specifying the unique occurrence of an event

- StatusCode – Return value of the library call.

  write(session: VISASession, data: [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.write)

Write data to device or interface synchronously.

Corresponds to viWrite function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – Data to be written.

Returns:

- int – Number of bytes actually transferred

- StatusCode – Return value of the library call.

  write_asynchronously(session: VISASession, data: [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[VISAJobID, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.write_asynchronously)

Write data to device or interface asynchronously.

Corresponds to viWriteAsync function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – Data to be written.

Returns:

- VISAJobID – Job ID of this asynchronous write operation

- StatusCode – Return value of the library call.
