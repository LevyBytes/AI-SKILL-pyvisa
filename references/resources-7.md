# Resources (part 7)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

**break_on_termchar** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Controls whether reading stops at a termination character instead of waiting for the message end. Defaults to False.

- **monitoring_interface** (SupportsUpdate Protocol**, **optional) – Progress monitor whose update() method receives the number of bytes read. The tqdm documentation describes a compatible progress-bar package.

Returns:

Bytes read from the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

read_raw(size: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

Read the unmodified string sent from the instrument to the computer.

In contrast to read(), no termination characters are stripped.

Parameters:

**size** (Optional\*\*[[int](https://docs.python.org/3/library/functions.html#int)]**, **optional) – Chunk size for this read operation. None means the resource-wide value is used.

Returns:

Bytes read from the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

read_stb() → [int](https://docs.python.org/3/library/functions.html#int)

Service request status register.

*property *read_termination*: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

Read termination character.

read_termination_context(new_termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)) → [Iterator](https://docs.python.org/3/library/typing.html#typing.Iterator)

*classmethod *register(interface_type: [InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType), resource_class: [str](https://docs.python.org/3/library/stdtypes.html#str)) → [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[[Type](https://docs.python.org/3/library/typing.html#typing.Type)[T]], [Type](https://docs.python.org/3/library/typing.html#typing.Type)[T]]

Create a decorator to register a class.

The class is associated to an interface type, resource class pair.

Parameters:

- **interface_type** ([constants.InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)) – Interface type for which to register a wrapper class.

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

send_end*: Attribute[[bool](https://docs.python.org/3/library/functions.html#bool)]*

Whether END is asserted while transferring the buffer's final byte.

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

*property *stb*: [int](https://docs.python.org/3/library/functions.html#int)*

Service request status register.

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

visa_attributes_classes*: ClassVar[Set[Type[attributes.Attribute]]]\*\* = {<class 'pyvisa.attributes.AttrVI_ATTR_DMA_ALLOW_EN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_FILE_APPEND_EN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_INTF_INST_NAME'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_INTF_NUM'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_INTF_TYPE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_IO_PROT'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_MAX_QUEUE_LENGTH'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_OPER_MODE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_SIZE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RM_SESSION'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_CLASS'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_IMPL_VERSION'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_LOCK_STATE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_ID'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_NAME'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_NAME'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_SPEC_VERSION'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_SEND_END_EN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_SUPPRESS_END_EN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TCPIP_ADDR'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TCPIP_DEVICE_NAME'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TCPIP_HISLIP_MAX_MESSAGE_KB'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TCPIP_HISLIP_OVERLAP_EN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TCPIP_HISLIP_VERSION'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TCPIP_HOSTNAME'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TCPIP_IS_HISLIP'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR_EN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TRIG_ID'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_OPER_MODE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_SIZE'>}*

Descriptor classes for VISA attributes; use them to inspect supported attributes and allowed values. Common descriptors are usually exposed directly on the resource.

visalib*: [VisaLibraryBase](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase)*

Will be present when used as a mixin with Resource

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

write(message: [str](https://docs.python.org/3/library/stdtypes.html#str), termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [int](https://docs.python.org/3/library/functions.html#int)

Write a string message to the device.

The write_termination is always appended to it.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to be sent.

- **termination** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Optional write termination override. None uses write_termination, and the default is None.

- **encoding** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Optional encoding override for converting str to bytes. None uses encoding, and the default is None.

Returns:

Number of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

write*ascii_values(message: [str](https://docs.python.org/3/library/stdtypes.html#str), <wbr>values: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[Any](https://docs.python.org/3/library/typing.html#typing.Any)], <wbr>converter: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['s', <wbr>'b', <wbr>'c', <wbr>'d', <wbr>'o', <wbr>'x', <wbr>'X', <wbr>'e', <wbr>'E', <wbr>'f', <wbr>'F', <wbr>'g', <wbr>'G'] | [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[[str](https://docs.python.org/3/library/stdtypes.html#str)], <wbr>[Any](https://docs.python.org/3/library/typing.html#typing.Any)] = 'f'*, <wbr>separator: [str](https://docs.python.org/3/library/stdtypes.html#str) | [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[[Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[str](https://docs.python.org/3/library/stdtypes.html#str)]], <wbr>[str](https://docs.python.org/3/library/stdtypes.html#str)] = ','\_, <wbr>termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, <wbr>encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None)

Write a string message, then append values formatted as ASCII data for the device.

The write_termination is always appended to it.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Header of the message to be sent.

- **values** (Sequence**[**Any\*\*]) – Data to be written to the device.

- **converter** (Union\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str), **Callable**[**[**Any**]**, \_[str](https://docs.python.org/3/library/stdtypes.html#str)]**]**, \*\*optional) – String format code or callable used to convert each value. Defaults to f.

- **separator** (Union\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str), **Callable**[**[**Iterable\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**]**, \_[str](https://docs.python.org/3/library/stdtypes.html#str)]**]**, \*\*optional) – str value or callable that combines all values into one str. When given a str, separator.join(values) is used. Defaults to comma.

- **termination** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Optional write termination override. None uses write_termination, and the default is None.

- **encoding** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Optional encoding override for converting str to bytes. None uses encoding, and the default is None.

Returns:

Number of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

write*binary_values(message: [str](https://docs.python.org/3/library/stdtypes.html#str), <wbr>values: [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[Any](https://docs.python.org/3/library/typing.html#typing.Any)], <wbr>datatype: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['s', <wbr>'b', <wbr>'B', <wbr>'h', <wbr>'H', <wbr>'i', <wbr>'I', <wbr>'l', <wbr>'L', <wbr>'q', <wbr>'Q', <wbr>'f', <wbr>'d'] = 'f'*, <wbr>is*big_endian: [bool](https://docs.python.org/3/library/functions.html#bool) = False, <wbr>termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, <wbr>encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, <wbr>header_fmt: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['ieee', <wbr>'hp', <wbr>'rs', <wbr>'empty'] = 'ieee'*)

Write a string message and then append values encoded in binary format for the device.

The write_termination is always appended to it.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The header of the message to be sent.

- **values** (Sequence**[**Any\*\*]) – Data to be written to the device.

- **datatype** (util.BINARY_DATATYPES**, **optional) – The format string for a single element. See struct module.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Are the data in big or little endian order.

- **termination** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Optional write termination override. None uses write_termination, and the default is None.

- **encoding** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Optional encoding override for converting str to bytes. None uses encoding, and the default is None.

- **header_fmt** (util.BINARY_HEADERS) – Format of the header prefixing the data.

Returns:

Number of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

write_raw(message: [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) → [int](https://docs.python.org/3/library/functions.html#int)

Write a byte message to the device.

Parameters:

**message** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – The message to be sent.

Returns:

Number of bytes written

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

*property *write_termination*: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Write termination character.

*class *pyvisa.resources.TCPIPSocket(resource_manager: [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager), resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str))[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/tcpip.html#TCPIPSocket)

Communicates with to devices of type TCPIP::host address::port::SOCKET

More complex resource names can be specified with the following grammar:

TCPIP[board]::host address::port::SOCKET

Do not instantiate directly, use [`pyvisa.highlevel.ResourceManager.open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource).

CR*: [str](https://docs.python.org/3/library/stdtypes.html#str)\*\* = '\r'*

LF*: [str](https://docs.python.org/3/library/stdtypes.html#str)\*\* = '\n'*

allow_dma*: Attribute[[bool](https://docs.python.org/3/library/functions.html#bool)]*

Should I/O accesses use DMA (True) or Programmed I/O (False).

assert_trigger() → [None](https://docs.python.org/3/library/constants.html#None)

Sends a software trigger to the device.

before_close() → [None](https://docs.python.org/3/library/constants.html#None)

Called just before closing an instrument.

chunk_size*: [int](https://docs.python.org/3/library/functions.html#int)\*\* = 20480*

Bytes requested per read chunk. Some resources, such as serial resources, may reject large chunk sizes.

clear() → [None](https://docs.python.org/3/library/constants.html#None)

Clear this resource.

close() → [None](https://docs.python.org/3/library/constants.html#None)

Closes the VISA session and marks the handle as invalid.

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

  enable_event(event_type: EventType, mechanism: EventMechanism, context: [None](https://docs.python.org/3/library/constants.html#None) = None) → [None](https://docs.python.org/3/library/constants.html#None)

Enable event occurrences for specified event types and mechanisms in this resource.

Parameters:

- **event_type** (constants.EventType) – Logical event identifier.

- **mechanism** (constants.EventMechanism) – Specifies event handling mechanisms to be enabled

- **context** (None) – Not currently used, leave as None.

  *property *encoding*: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Encoding used for read and write operations.

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
