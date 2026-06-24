# Visalibrarybase (part 1)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

### Visa Library

*class *pyvisa.highlevel.VisaLibraryBase(library*path: [str](https://docs.python.org/3/library/stdtypes.html#str) | LibraryPath = ''*)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase)

Base for VISA library classes.

A class derived from VisaLibraryBase supplies low-level device communication through Pythonic wrappers around VISA functions. Derived classes may leave unsupported methods unimplemented. Methods normally return status codes, but on errors they should raise the matching exception because that is the Pythonic behavior.

The default VisaLibrary class is `pyvisa.ctwrapper.highlevel.IVIVisaLibrary`, a ctypes wrapper for the IVI-VISA library. IVI-VISA may be NI-VISA, Keysight VISA, R&S VISA, tekVISA, or another vendor implementation.

Usually, do not instantiate this object directly. User code normally works with [`pyvisa.highlevel.ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager). When necessary, retrieve the VISA library from that manager:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager("/path/to/my/libvisa.so.7")
>>> lib = rm.visalib

```

assert_interrupt_signal(session: VISASession, mode: AssertSignalInterrupt, status_id: [int](https://docs.python.org/3/library/functions.html#int)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.assert_interrupt_signal)

Asserts the specified interrupt or signal.

Corresponds to viAssertIntrSignal function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mode** (constants.AssertSignalInterrupt) – How to assert the interrupt.

- **status_id** ([int](https://docs.python.org/3/library/functions.html#int)) – Status value to be presented during an interrupt acknowledge cycle.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

assert_trigger(session: VISASession, protocol: TriggerProtocol) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.assert_trigger)

Assert software or hardware trigger.

Corresponds to viAssertTrigger function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **protocol** (constants.TriggerProtocol) – Trigger protocol to use during assertion.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

assert_utility_signal(session: VISASession, line: UtilityBusSignal) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.assert_utility_signal)

Assert or deassert the specified utility bus signal.

Corresponds to viAssertUtilSignal function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **line** (constants.UtilityBusSignal) – Specifies the utility bus signal to assert.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

buffer_read(session: VISASession, count: [int](https://docs.python.org/3/library/functions.html#int)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[bytes](https://docs.python.org/3/library/stdtypes.html#bytes), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.buffer_read)

Reads data through the use of a formatted I/O read buffer.

The data can be read from a device or an interface.

Corresponds to viBufRead function of the VISA library.

Parameters:

- **session** (VISASession Unique logical identifier to a session.\_)

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to be read.

Returns:

- dbytes – Data read

- StatusCode – Return value of the library call.

  buffer_write(session: VISASession, data: [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.buffer_write)

Writes data to a formatted I/O write buffer synchronously.

Corresponds to viBufWrite function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – Data to be written.

Returns:

- int – number of written bytes

- StatusCode – return value of the library call.

  clear(session: VISASession) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.clear)

Clears a device.

Corresponds to viClear function of the VISA library.

Parameters:

**session** (VISASession) – Unique logical identifier to a session.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

close(session: VISASession | VISAEventContext | VISARMSession) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.close)

Closes the specified session, event, or find list.

Corresponds to viClose function of the VISA library.

Parameters:

**session** (Union**[**VISASession**, **VISAEventContext**, **VISARMSession\*\*]) – Unique logical identifier for a session, event, or resource manager.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

disable_event(session: VISASession, event_type: EventType, mechanism: EventMechanism) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.disable_event)

Disable notification for an event type(s) via the specified mechanism(s).

Corresponds to viDisableEvent function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **event_type** (constants.EventType) – Event type.

- **mechanism** (constants.EventMechanism) – Event handling mechanisms to be disabled.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

discard_events(session: VISASession, event_type: EventType, mechanism: EventMechanism) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.discard_events)

Discard event occurrences for a given type and mechanisms in a session.

Corresponds to viDiscardEvents function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **event_type** (constants.EventType) – Logical event identifier.

- **mechanism** (constants.EventMechanism) – Specifies event handling mechanisms to be discarded.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

enable_event(session: VISASession, event_type: EventType, mechanism: EventMechanism, context: [None](https://docs.python.org/3/library/constants.html#None) = None) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.enable_event)

Enable event occurrences for specified event types and mechanisms in a session.

Corresponds to viEnableEvent function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **event_type** (constants.EventType) – Logical event identifier.

- **mechanism** (constants.EventMechanism) – Specifies event handling mechanisms to be enabled.

- **context** (None**, **optional) – Unused parameter…

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

flush(session: VISASession, mask: BufferOperation) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.flush)

Flush the specified buffers.

These buffers may belong to formatted I/O operations, serial communication, or both.

Corresponds to viFlush function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mask** (constants.BufferOperation) – Specifies which buffer-flush action to perform. The values can be combined using the | operator, but multiple operations targeting one buffer cannot be combined.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

get_attribute(session: VISASession | VISAEventContext | VISARMSession, attribute: ResourceAttribute | EventAttribute) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[Any](https://docs.python.org/3/library/typing.html#typing.Any), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.get_attribute)

Retrieves the state of an attribute.

Corresponds to viGetAttribute function of the VISA library.

Parameters:

- **session** (Union**[**VISASession**, **VISAEventContext\*\*]) – Unique logical identifier for a session, event, or find list.

- **attribute** (Union**[**constants.ResourceAttribute**, **constants.EventAttribute\*\*]) – Resource or event attribute whose current state is requested.

Returns:

- Any – State of the queried attribute for a specified resource

- StatusCode – Return value of the library call.

  get_buffer_from_id(job_id: VISAJobID) → [SupportsBytes](https://docs.python.org/3/library/typing.html#typing.SupportsBytes) | [None](https://docs.python.org/3/library/constants.html#None)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.get_buffer_from_id)

Retrieve the buffer associated with a job id created in read_asynchronously

Parameters:

**job_id** (VISAJobID) – Id of the job for which to retrieve the buffer.

Returns:

Buffer holding the data, or None when the job id is not linked to any job.

Return type:

Optional[SupportsBytes]

*static *get_debug_info() → [List](https://docs.python.org/3/library/typing.html#typing.List)[[str](https://docs.python.org/3/library/stdtypes.html#str)] | [Dict](https://docs.python.org/3/library/typing.html#typing.Dict)[[str](https://docs.python.org/3/library/stdtypes.html#str), [Any](https://docs.python.org/3/library/typing.html#typing.Any)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.get_debug_info)

Override to return an iterable of lines with the backend debug details.

get_last_status_in_session(session: VISASession | VISARMSession) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.get_last_status_in_session)

Last status in session.

Helper function to be called by resources properties.

*static *get_library_paths() → [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[LibraryPath][source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.get_library_paths)

Override to list the possible library_paths if no path is specified.

gpib_command(session: VISASession, data: [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.gpib_command)

Write GPIB command bytes on the bus.

Corresponds to viGpibCommand function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – Data to write.

Returns:

- int – Number of written bytes

- StatusCode – Return value of the library call.

  gpib_control_atn(session: VISASession, mode: ATNLineOperation) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.gpib_control_atn)

Specifies the ATN line state together with the local active-controller state.

Corresponds to viGpibControlATN function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mode** (constants.ATNLineOperation) – State for the ATN line and, optionally, the local active-controller state.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

gpib_control_ren(session: VISASession, mode: RENLineOperation) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.gpib_control_ren)

Controls the state of the GPIB Remote Enable (REN) interface line.

Optionally the remote/local state of the device can also be set.

Corresponds to viGpibControlREN function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **mode** (constants.RENLineOperation) – State for the REN line and, optionally, the device remote/local state.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

gpib_pass_control(session: VISASession, primary_address: [int](https://docs.python.org/3/library/functions.html#int), secondary_address: [int](https://docs.python.org/3/library/functions.html#int)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.gpib_pass_control)

Tell a GPIB device to become controller in charge (CIC).

Corresponds to viGpibPassControl function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **primary_address** ([int](https://docs.python.org/3/library/functions.html#int)) – Primary address of the GPIB device to which you want to pass control.

- **secondary_address** ([int](https://docs.python.org/3/library/functions.html#int)) – Secondary address for the targeted GPIB device. If that device has no secondary address, this parameter should contain the value Constants.VI_NO_SEC_ADDR.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

gpib_send_ifc(session: VISASession) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.gpib_send_ifc)

Pulse the interface clear line (IFC) for at least 100 microseconds.

Corresponds to viGpibSendIFC function of the VISA library.

Parameters:

**session** (VISASession) – Unique logical identifier to a session.

Returns:

Return value of the library call.

Return type:

[StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

handle_return_value(session: VISAEventContext | VISARMSession | VISASession | [None](https://docs.python.org/3/library/constants.html#None), status_code: [int](https://docs.python.org/3/library/functions.html#int)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.handle_return_value)

Helper function handling the return code of a low-level operation.

Used when implementing concrete subclasses of VISALibraryBase.

handlers*: [DefaultDict](https://docs.python.org/3/library/typing.html#typing.DefaultDict)[VISASession, [List](https://docs.python.org/3/library/typing.html#typing.List)[[Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)], [Any](https://docs.python.org/3/library/typing.html#typing.Any), [Any](https://docs.python.org/3/library/typing.html#typing.Any), [Any](https://docs.python.org/3/library/typing.html#typing.Any)]]]*

Contains all installed event handlers. Each entry is a four-element tuple: the handler itself as a Python callable, the user handle in a form meaningful to the lower-level implementation such as a ctypes object for the ctypes backend, the handler converted for backend use such as a CFUNCTYPE-created ctypes object for the ctypes backend, and the event type.

ignore_warning(session: VISASession | VISARMSession, \*warnings_constants: [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)) → [Iterator](https://docs.python.org/3/library/typing.html#typing.Iterator)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.ignore_warning)

Ignore warnings for a session for the duration of the context.

Parameters:

- **session** (Union**[**VISASession**, **VISARMSession\*\*]) – Unique logical identifier to a session.

- **warnings_constants** ([StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)) – Constants identifying the warnings to ignore.

  in_16(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.in_16)

Reads a 16-bit value from the selected memory space and offset.

Corresponds to viIn16\* function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Specifies the address space.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; False by default.

Returns:

- int – Data read from memory

- StatusCode – Return value of the library call.

  in_32(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.in_32)

Reads a 32-bit value from the selected memory space and offset.

Corresponds to viIn32\* function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Specifies the address space.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; False by default.

Returns:

- int – Data read from memory

- StatusCode – Return value of the library call.

  in_64(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.in_64)

Reads a 64-bit value from the selected memory space and offset.

Corresponds to viIn64\* function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Specifies the address space.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) for the address or register to read from.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for offsets regardless of platform; False by default.

Returns:

- int – Data read from memory

- StatusCode – Return value of the library call.

  in_8(session: VISASession, space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#VisaLibraryBase.in_8)

Reads an 8-bit value from the selected memory space and offset.

Corresponds to viIn8\* function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **space** (constants.AddressSpace) – Specifies the address space.

-
