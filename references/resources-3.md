# Resources (part 3)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

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

write(message: [str](https://docs.python.org/3/library/stdtypes.html#str), termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [int](https://docs.python.org/3/library/functions.html#int)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.write)

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

write*ascii_values(message: [str](https://docs.python.org/3/library/stdtypes.html#str), <wbr>values: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[Any](https://docs.python.org/3/library/typing.html#typing.Any)], <wbr>converter: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['s', <wbr>'b', <wbr>'c', <wbr>'d', <wbr>'o', <wbr>'x', <wbr>'X', <wbr>'e', <wbr>'E', <wbr>'f', <wbr>'F', <wbr>'g', <wbr>'G'] | [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[[str](https://docs.python.org/3/library/stdtypes.html#str)], <wbr>[Any](https://docs.python.org/3/library/typing.html#typing.Any)] = 'f'*, <wbr>separator: [str](https://docs.python.org/3/library/stdtypes.html#str) | [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[[Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[str](https://docs.python.org/3/library/stdtypes.html#str)]], <wbr>[str](https://docs.python.org/3/library/stdtypes.html#str)] = ','\_, <wbr>termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, <wbr>encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.write_ascii_values)

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

write*binary_values(message: [str](https://docs.python.org/3/library/stdtypes.html#str), <wbr>values: [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[Any](https://docs.python.org/3/library/typing.html#typing.Any)], <wbr>datatype: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['s', <wbr>'b', <wbr>'B', <wbr>'h', <wbr>'H', <wbr>'i', <wbr>'I', <wbr>'l', <wbr>'L', <wbr>'q', <wbr>'Q', <wbr>'f', <wbr>'d'] = 'f'*, <wbr>is*big_endian: [bool](https://docs.python.org/3/library/functions.html#bool) = False, <wbr>termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, <wbr>encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, <wbr>header_fmt: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['ieee', <wbr>'hp', <wbr>'rs', <wbr>'empty'] = 'ieee'*)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.write_binary_values)

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

write_raw(message: [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) → [int](https://docs.python.org/3/library/functions.html#int)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.write_raw)

Write a byte message to the device.

Parameters:

**message** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – The message to be sent.

Returns:

Number of bytes written

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

*property *write_termination*: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Write termination character.

*class *pyvisa.resources.RegisterBasedResource(resource_manager: [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager), resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str))[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/registerbased.html#RegisterBasedResource)

Base class for resources that use register based communication.

before_close() → [None](https://docs.python.org/3/library/constants.html#None)

Called just before closing an instrument.

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

move_in(space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), width: DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [List](https://docs.python.org/3/library/typing.html#typing.List)[[int](https://docs.python.org/3/library/functions.html#int)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/registerbased.html#RegisterBasedResource.move_in)

Copy a block from the specified address space and offset into local memory.

Corresponds to viMoveIn\* functions of the VISA library.

Parameters:

- **space** (constants.AddressSpace) – Address space from which to move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Byte offset for the address or register being read.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Element count to transfer; each element uses the same data width as the source.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) – Bits per element for the transfer.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for the offset regardless of platform. Defaults to False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (constants.StatusCode) – Return value of the library call.

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

move_out(space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), data: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[int](https://docs.python.org/3/library/functions.html#int)], width: DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/registerbased.html#RegisterBasedResource.move_out)

Copy a local memory block into the specified address space and offset.

Corresponds to viMoveOut\* functions of the VISA library.

Parameters:

- **space** (constants.AddressSpace) – Address space into which move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Byte offset for the address or register being read.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – Element count to transfer; each element uses the same data width as the source.

- **data** (Iterable\*\*[[int](https://docs.python.org/3/library/functions.html#int)]) – Data to write to bus.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) – Bits per element for the transfer.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for the offset regardless of platform. Defaults to False.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

open(access_mode: [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes) = AccessModes.no_lock, open_timeout: [int](https://docs.python.org/3/library/functions.html#int) = 5000) → [None](https://docs.python.org/3/library/constants.html#None)

Opens a session to the specified resource.

Parameters:

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), \*\*optional) – Access mode to use for the resource; defaults to constants.AccessModes.no_lock.

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – When `access_mode` asks for a lock, this is the millisecond wait before the open operation fails because the resource stayed locked. Defaults to 5000.

  read_memory(space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), width: DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [int](https://docs.python.org/3/library/functions.html#int)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/registerbased.html#RegisterBasedResource.read_memory)

Read a value from the specified memory space and offset.

Parameters:

- **space** (constants.AddressSpace) – Specifies the address space from which to read.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) – Byte offset for the address or register being read.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) – Bits per element for the transfer.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits for the offset regardless of platform. Defaults to False.

Returns:

**data** – Data read from memory

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

*classmethod *register(interface_type: [InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType), resource_class: [str](https://docs.python.org/3/library/stdtypes.html#str)) → [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[[Type](https://docs.python.org/3/library/typing.html#typing.Type)[T]], [Type](https://docs.python.org/3/library/typing.html#typing.Type)[T]]

Create a decorator to register a class.

The class is associated to an interface type, resource class pair.

Parameters:

-
