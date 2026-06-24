# Resources (part 4)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

**interface_type** ([constants.InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)) – Interface type for which to register a wrapper class.

- **resource_class** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Resource class for which to register a wrapper class.

Returns:

Decorator that registers the class and raises TypeError when required VISA attributes are absent.

Return type:

Callable[[Type[T]], Type[T]]

resource_class*: Attribute[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

Resource class (for example, “INSTR”) as defined by the canonical resource name.

*property *resource_info*: [ResourceInfo](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceInfo)*

Get the extended information of this resource.

resource_manager*: [highlevel.ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager)*

Reference to the resource manager used by this resource

resource_manufacturer_name*: Attribute[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

Manufacturer name of the vendor that implemented the VISA library.

resource_name*: Attribute[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

Unique identifier for a resource compliant with the address structure.

*property *session*: VISASession*

Resource session handle.

Raises:

**errors.InvalidSession** – Raised if session is closed.

set_visa_attribute(name: ResourceAttribute, state: [Any](https://docs.python.org/3/library/typing.html#typing.Any)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Set the state of an attribute.

Prefer the dedicated descriptor for common attributes because it validates values and performs automatic conversions.

Parameters:

- **name** (constants.ResourceAttribute) – Attribute for which the state is to be modified.

- **state** (Any) – State value to assign to the requested attribute for this object.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

spec_version*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Version of the VISA specification to which the implementation is compliant.

timeout*: Attribute[[float](https://docs.python.org/3/library/functions.html#float)]*

Timeout in milliseconds for all resource I/O operations.

uninstall_handler(event_type: EventType, handler: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)], user_handle=None) → [None](https://docs.python.org/3/library/constants.html#None)

Uninstalls handlers for events in this resource.

Parameters:

- **event_type** (constants.EventType) – Logical event identifier.

- **handler** (VISAHandler) – Handler function to be uninstalled by a client application.

- **user_handle** (Any) – The user handle returned by install_handler.

  unlock() → [None](https://docs.python.org/3/library/constants.html#None)

Relinquishes a lock for the specified resource.

visa_attributes_classes*: ClassVar[Set[Type[attributes.Attribute]]]\*\* = {<class 'pyvisa.attributes.AttrVI_ATTR_INTF_INST_NAME'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_INTF_NUM'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_INTF_TYPE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_MAX_QUEUE_LENGTH'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RM_SESSION'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_CLASS'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_IMPL_VERSION'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_LOCK_STATE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_ID'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_NAME'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_NAME'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_SPEC_VERSION'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>}*

Descriptor classes for VISA attributes; use them to inspect supported attributes and allowed values. Common descriptors are usually exposed directly on the resource.

visalib*: [highlevel.VisaLibraryBase](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase)*

Reference to the VISA library instance used by the resource

wait_on_event(in_event_type: EventType, timeout: [int](https://docs.python.org/3/library/functions.html#int), capture_timeout: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → WaitResponse

Waits for an occurrence of the specified event in this resource.

in_event_typeconstants.EventType

Logical identifier of the event(s) to wait for.

timeoutint

Maximum wait, expressed in time units, for the requested event before a time-elapsed error is returned. The unit is milliseconds; None waits indefinitely when needed.

capture_timeoutbool, optional

When True, a timeout returns a WaitResponse with timed_out=True instead of raising VisaIOError(VI_ERROR_TMO).

Returns:

Object that contains event_type, context and ret value.

Return type:

WaitResponse

wrap_handler(callable: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[Resource, Event, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]) → [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]

Wrap an event handler to provide the signature expected by VISA.

Expected handler signature: handler(resource: Resource, event: Event, user_handle: Any) -> None.

Use the wrapped handler only for events produced by the resource that created the wrapper.

write_memory(space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), data: [int](https://docs.python.org/3/library/functions.html#int), width: DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/registerbased.html#RegisterBasedResource.write_memory)

Write a value to the specified memory space and offset.

Parameters:

- **space** (constants.AddressSpace) – Specifies the address space.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Byte offset for the address or register being read.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) – Bits per element for the transfer.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for the offset regardless of platform. Defaults to False.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

*class *pyvisa.resources.SerialInstrument(resource_manager: [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager), resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str))[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/serial.html#SerialInstrument)

Communicates with devices of type ASRL<board>[::INSTR]

Do not instantiate directly, use [`pyvisa.highlevel.ResourceManager.open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource).

CR*: [str](https://docs.python.org/3/library/stdtypes.html#str)\*\* = '\r'*

LF*: [str](https://docs.python.org/3/library/stdtypes.html#str)\*\* = '\n'*

allow_dma*: Attribute[[bool](https://docs.python.org/3/library/functions.html#bool)]*

Should I/O accesses use DMA (True) or Programmed I/O (False).

allow_transmit*: Attribute[[bool](https://docs.python.org/3/library/functions.html#bool)]*

Manually control transmission. The default value is True.

assert_trigger() → [None](https://docs.python.org/3/library/constants.html#None)

Sends a software trigger to the device.

baud_rate*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Baud rate of the interface. The default value is 9600.

before_close() → [None](https://docs.python.org/3/library/constants.html#None)

Called just before closing an instrument.

break_length*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Duration (in milliseconds) of the break signal. The default value is 250.

break_state*: Attribute[[LineState](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.LineState)]*

Manually sets the break signal assertion state. Defaults to constants.LineState.unasserted (VI_STATE_UNASSERTED).

bytes_in_buffer*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Number of bytes available in the low- level I/O receive buffer.

chunk_size*: [int](https://docs.python.org/3/library/functions.html#int)\*\* = 20480*

Bytes requested per read chunk. Some resources, such as serial resources, may reject large chunk sizes.

clear() → [None](https://docs.python.org/3/library/constants.html#None)

Clear this resource.

close() → [None](https://docs.python.org/3/library/constants.html#None)

Closes the VISA session and marks the handle as invalid.

data_bits*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Data bits in each frame, from 5 to 8. The default value is 8.

disable_event(event_type: EventType, mechanism: EventMechanism) → [None](https://docs.python.org/3/library/constants.html#None)

Disable notification for an event type(s) via the specified mechanism(s).

Parameters:

- **event_type** (constants.EventType) – Logical event identifier.

- **mechanism** (constants.EventMechanism) – Specifies event handling mechanisms to be disabled.

  discard_events(event_type: EventType, mechanism: EventMechanism) → [None](https://docs.python.org/3/library/constants.html#None)

Discards event occurrences for an event type and mechanism in this resource.

Parameters:

- **event_type** (constants.EventType) – Logical event identifier.

- **mechanism** (constants.EventMechanism) – Specifies event handling mechanisms to be disabled.

  discard_null*: Attribute[[bool](https://docs.python.org/3/library/functions.html#bool)]*

If set to True, NUL characters are discarded. The default is False.

enable_event(event_type: EventType, mechanism: EventMechanism, context: [None](https://docs.python.org/3/library/constants.html#None) = None) → [None](https://docs.python.org/3/library/constants.html#None)

Enable event occurrences for specified event types and mechanisms in this resource.

Parameters:

- **event_type** (constants.EventType) – Logical event identifier.

- **mechanism** (constants.EventMechanism) – Specifies event handling mechanisms to be enabled

- **context** (None) – Not currently used, leave as None.

  *property *encoding*: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Encoding used for read and write operations.

end_input*: Attribute[[SerialTermination](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.SerialTermination)]*

Method used to terminate read operations. The default value is constants.SerialTermination.termination_char (VI_ASRL_END_TERMCHAR).

end_output*: Attribute[[SerialTermination](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.SerialTermination)]*

Write-operation termination method. The default, constants.SerialTermination.none (VI_ASRL_END_NONE), ends after all requested data transfers or an error occurs.

flow_control*: Attribute[ControlFlow]*

Flow-control type used by the transfer mechanism. The default is constants.ControlFlow.none (VI_ASRL_FLOW_NONE).

flush(mask: BufferOperation) → [None](https://docs.python.org/3/library/constants.html#None)

Manually clears the specified buffers.

Some mask values also cause buffered data to be written out to the device.

Parameters:

**mask** (constants.BufferOperation) – Buffer-flush action to perform. See highlevel.VisaLibraryBase.flush for the full behavior.

get_visa_attribute(name: ResourceAttribute) → [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Retrieves the state of an attribute in this resource.

Prefer the dedicated descriptor for common attributes because it validates values and performs automatic conversions.

Parameters:

**name** (constants.ResourceAttribute) – Resource attribute for which the state query is made.

Returns:

The state of the queried attribute for a specified resource.

Return type:

Any

ignore_warning(\*warnings_constants: [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)) → [ContextManager](https://docs.python.org/3/library/typing.html#typing.ContextManager)

Ignoring warnings context manager for the current resource.

Parameters:

**warnings_constants** ([constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)) – Constants identifying the warnings to ignore.

implementation_version*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Resource version that identifies the revisions or implementations of a resource.

install_handler(event_type: EventType, handler: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)], user_handle=None) → [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Install handlers for event callbacks in this resource.

Parameters:

- **event_type** (constants.EventType) – Logical event identifier.

- **handler** (VISAHandler) – Handler function to be installed by a client application.

- **user_handle** – Application-supplied value used to distinguish handlers for the same event type. Backends may restrict allowed values; see the backend install_visa_handler details.

Returns:

Backend-ready representation of the user handle. Use this representation when uninstalling a handler.

Return type:

Any

interface_number*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Board number for the given interface.

interface_type*: Attribute[[constants.InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)]*

Interface type of the given session.

io_protocol*: Attribute[[constants.IOProtocol](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.IOProtocol)]*

IO protocol to use. See the attribute definition for more details.

*property *last_status*: [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)*

Last status code for this session.

lock(timeout: [float](https://docs.python.org/3/library/functions.html#float) | [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['default'] = 'default'\_, requested_key: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [str](https://docs.python.org/3/library/stdtypes.html#str)

Establish a shared lock to the resource.

Parameters:

- **timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) – How long, in milliseconds, the resource should wait for the locking session to release it before reporting an error. The "default" value uses self.timeout.

- **requested_key** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Key from another session when this session should share that lock; use None to create a fresh shared access key.

Returns:

Returns a newly generated shared access key when requested_key is None; otherwise returns requested_key.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

lock*context(timeout: [float](https://docs.python.org/3/library/functions.html#float) | [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['default'] = 'default'*, requested*key: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = 'exclusive'*) → [Iterator](https://docs.python.org/3/library/typing.html#typing.Iterator)[[str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)]

A context that locks

Parameters:

- **timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) – How long, in milliseconds, the resource should wait for the locking session to release it before reporting an error. The "default" value uses self.timeout.

- **requested_key** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – With the default value "exclusive", the context takes an exclusive lock. Any other value is treated as the shared-lock key, while None asks the backend to create a new shared access key.

Yields:

Optional[str] – The access_key if applicable.

lock*excl(timeout: [float](https://docs.python.org/3/library/functions.html#float) | [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['default'] = 'default'*) → [None](https://docs.python.org/3/library/constants.html#None)

Establish an exclusive lock to the resource.

Parameters:

**timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) – How long, in milliseconds, the resource should wait for the locking session to release it before reporting an error. The "default" value uses self.timeout.

lock_state*: Attribute[[constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes)]*

Current locking state of the resource.

open(access_mode: [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes) = AccessModes.no_lock, open_timeout: [int](https://docs.python.org/3/library/functions.html#int) = 5000) → [None](https://docs.python.org/3/library/constants.html#None)

Opens a session to the specified resource.

Parameters:

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), \*\*optional) – Access mode to use for the resource; defaults to constants.AccessModes.no_lock.

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – When `access_mode` asks for a lock, this is the millisecond wait before the open operation fails because the resource stayed locked. Defaults to 5000.

  parity*: Attribute[[Parity](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.Parity)]*

Parity setting for transmitted and received frames. The default is constants.Parity.none (VI_ASRL_PAR_NONE).

query(message: [str](https://docs.python.org/3/library/stdtypes.html#str), delay: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [str](https://docs.python.org/3/library/stdtypes.html#str)

A combination of write(message) and read()

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **delay** (Optional\*\*[[float](https://docs.python.org/3/library/functions.html#float)]**, **optional) – Seconds to pause between the write phase and the read phase. None uses self.query_delay.

Returns:

Answer from the device.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

query_ascii_values(message: str, <wbr>converter: ~typing.Literal['s', <wbr>'b', <wbr>'c', <wbr>'d', <wbr>'o', <wbr>'x', <wbr>'X', <wbr>'e', <wbr>'E', <wbr>'f', <wbr>'F', <wbr>'g', <wbr>'G'] | ~typing.Callable[[str], <wbr>~typing.Any] = 'f', <wbr>separator: str | ~typing.Callable[[str], <wbr>~typing.Iterable[str]] = ',', <wbr>container: ~typing.Type | ~typing.Callable[[~typing.Iterable], <wbr>~typing.Sequence] = <class 'list'>, <wbr>delay: float | None = None) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[Any](https://docs.python.org/3/library/typing.html#typing.Any)]

Query the device and return parsed ASCII-format values as an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **converter** (ASCII_CONVERTER**, **optional) – String format code or callable used to convert each value. Defaults to f.

- **separator** (Union\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str), **Callable**[\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **Iterable\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**]**]) – Separator policy for converting the returned text into elements. A str is passed to data.split(separator); the default is comma.

- **container** (Union**[**Type**, **Callable**[**[**Iterable**]**, **Sequence**]**]**, **optional) – Container used for the parsed output, such as list, tuple, or np.ndarray. The default container is list.

- **delay** (Optional\*\*[[float](https://docs.python.org/3/library/functions.html#float)]**, **optional) – Seconds to pause between the write phase and the read phase. None uses self.query_delay.

Returns:

Parsed data.

Return type:

Sequence

query_binary_values(message: str, <wbr>datatype: ~typing.Literal['s', <wbr>'b', <wbr>'B', <wbr>'h', <wbr>'H', <wbr>'i', <wbr>'I', <wbr>'l', <wbr>'L', <wbr>'q', <wbr>'Q', <wbr>'f', <wbr>'d'] = 'f', <wbr>is_big_endian: bool = False, <wbr>container: ~typing.Type | ~typing.Callable[[~typing.Iterable], <wbr>~typing.Sequence] = <class 'list'>, <wbr>delay: float | None = None, <wbr>header_fmt: ~typing.Literal['ieee', <wbr>'hp', <wbr>'rs', <wbr>'empty'] = 'ieee', <wbr>expect_termination: bool = True, <wbr>data_points: int = 0, <wbr>chunk_size: int | None = None, <wbr>monitoring_interface: ~pyvisa.resources.messagebased.SupportsUpdate | None = None, <wbr>length_before_block: int | None = None, <wbr>raise_on_late_block: bool = False) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[int](https://docs.python.org/3/library/functions.html#int) | [float](https://docs.python.org/3/library/functions.html#float)]

Query the device and return parsed binary-format values as an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **datatype** (BINARY_DATATYPES**, **optional) – Single-element format string; see the struct module. The default is f.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Are the data in big or little endian order. Defaults to False.

- **container** (Union**[**Type**, **Callable**[**[**Iterable**]**, **Sequence**]**]**, **optional) – Container used for the parsed output, such as list, tuple, or np.ndarray. The default container is list.

-
