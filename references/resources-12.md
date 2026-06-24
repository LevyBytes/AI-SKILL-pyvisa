# Resources (part 12)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

**break_on_termchar** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Stop reading when either a termination character appears or the message ends. Defaults to False.

- **monitoring_interface** (SupportsUpdate Protocol**, **optional) – Progress monitor object with update() method accepting the bytes-read count. See the tqdm documentation (a progress bar package) for details.

Returns:

Bytes read from the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

read_raw(size: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

Read the unmodified string sent from the instrument to the computer.

In contrast to read(), no termination characters are stripped.

Parameters:

**size** (Optional\*\*[[int](https://docs.python.org/3/library/functions.html#int)]**, **optional) – Chunk size used for reading. Defaults to None, meaning the resource-wide setting is used.

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

Whether to assert END while transferring the buffer’s final byte.

serial_number*: Attribute[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

USB serial number of this device.

*property *session*: VISASession*

Resource session handle.

Raises:

**errors.InvalidSession** – Raised if session is closed.

set_visa_attribute(name: ResourceAttribute, state: [Any](https://docs.python.org/3/library/typing.html#typing.Any)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Set the state of an attribute.

For frequently used attributes, prefer the dedicated descriptor because it checks values and performs automatic conversion.

Parameters:

- **name** (constants.ResourceAttribute) – Attribute for which the state is to be modified.

- **state** (Any) – Attribute state to set on the specified object.

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

usb_protocol*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

USB protocol used by this USB interface.

`visa_attributes_classes*: ClassVar[Set[Type[attributes.Attribute]]]** = {<class 'pyvisa.attributes.AttrVI_ATTR_DMA_ALLOW_EN'>, <class 'pyvisa.attributes.AttrVI_ATTR_FILE_APPEND_EN'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_INST_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_NUM'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_TYPE'>, <class 'pyvisa.attributes.AttrVI_ATTR_IO_PROT'>, <class 'pyvisa.attributes.AttrVI_ATTR_MANF_ID'>, <class 'pyvisa.attributes.AttrVI_ATTR_MANF_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_MAX_QUEUE_LENGTH'>, <class 'pyvisa.attributes.AttrVI_ATTR_MODEL_CODE'>, <class 'pyvisa.attributes.AttrVI_ATTR_MODEL_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_OPER_MODE'>, <class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_SIZE'>, <class 'pyvisa.attributes.AttrVI_ATTR_RM_SESSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_CLASS'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_IMPL_VERSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_LOCK_STATE'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_ID'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_SPEC_VERSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_SEND_END_EN'>, <class 'pyvisa.attributes.AttrVI_ATTR_SUPPRESS_END_EN'>, <class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR'>, <class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR_EN'>, <class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_ALT_SETTING'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_BULK_IN_PIPE'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_BULK_IN_STATUS'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_BULK_OUT_PIPE'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_BULK_OUT_STATUS'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_CLASS'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_CTRL_PIPE'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_END_IN'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_INTFC_NUM'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_INTR_IN_PIPE'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_INTR_IN_STATUS'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_MAX_INTR_SIZE'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_NUM_INTFCS'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_NUM_PIPES'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_PROTOCOL'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_SERIAL_NUM'>, <class 'pyvisa.attributes.AttrVI_ATTR_USB_SUBCLASS'>, <class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>, <class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_OPER_MODE'>, <class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_SIZE'>}*`

VISA attribute descriptor classes for inspecting supported attributes and allowed values. Commonly used attributes are usually exposed directly on the resource.

visalib*: [highlevel.VisaLibraryBase](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase)*

Reference to the VISA library instance used by the resource

wait_on_event(in_event_type: EventType, timeout: [int](https://docs.python.org/3/library/functions.html#int), capture_timeout: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → WaitResponse

Waits for an occurrence of the specified event in this resource.

in_event_typeconstants.EventType

Logical identifier of the event(s) to wait for.

timeoutint

Time in milliseconds that the resource waits for the requested event before returning a time elapsed error. None waits forever if necessary.

capture_timeoutbool, optional

When True, return a WaitResponse with timed_out=True instead of raising VisaIOError(VI_ERROR_TMO).

Returns:

Object that contains event_type, context and ret value.

Return type:

WaitResponse

wrap_handler(callable: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[Resource, Event, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]) → [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]

Wrap an event handler to provide the signature expected by VISA.

The handler must match this signature: handler(resource: Resource, event: Event, user_handle: Any) -> None.

Use the wrapped handler only for events from the same resource that created the wrapper.

write(message: [str](https://docs.python.org/3/library/stdtypes.html#str), termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [int](https://docs.python.org/3/library/functions.html#int)

Write a string message to the device.

The write_termination is always appended to it.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to be sent.

- **termination** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Character termination override. If None, write_termination supplies the value. Defaults to None.

- **encoding** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Encoding override for converting str to bytes. If None, encoding supplies the value. Defaults to None.

Returns:

Number of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

`write_ascii_values`(message: [str](https://docs.python.org/3/library/stdtypes.html#str), values: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[Any](https://docs.python.org/3/library/typing.html#typing.Any)], converter: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)`['s', 'b', 'c', 'd', 'o', 'x', 'X', 'e', 'E', 'f', 'F', 'g', 'G'] = 'f'` | [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[[str](https://docs.python.org/3/library/stdtypes.html#str)], [Any](https://docs.python.org/3/library/typing.html#typing.Any)], separator: [str](https://docs.python.org/3/library/stdtypes.html#str) | [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[[Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[str](https://docs.python.org/3/library/stdtypes.html#str)]], [str](https://docs.python.org/3/library/stdtypes.html#str)] = ','\_, termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None)

Write a string message and append ASCII-formatted values to the device.

The write_termination is always appended to it.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Header of the message to be sent.

- **values** (Sequence**[**Any\*\*]) – Data to be written to the device.

- **converter** (Union\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str), **Callable**[**[**Any**]**, \_[str](https://docs.python.org/3/library/stdtypes.html#str)]**]**, \*\*optional) – str formatting codes or a callable for converting each value. Defaults to “f”.

- **separator** (Union\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str), **Callable**[**[**Iterable\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**]**, \_[str](https://docs.python.org/3/library/stdtypes.html#str)]**]**, \*\*optional) – str or callable that joins the values into one str. With a str, separator.join(values) is used. Defaults to ‘,’

- **termination** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Character termination override. If None, write_termination supplies the value. Defaults to None.

- **encoding** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Encoding override for converting str to bytes. If None, encoding supplies the value. Defaults to None.

Returns:

Number of bytes written.

Return type:

[int](https://docs.python.org/3/library/functions.html#int)

`write_binary_values`(message: [str](https://docs.python.org/3/library/stdtypes.html#str), values: [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[Any](https://docs.python.org/3/library/typing.html#typing.Any)], datatype: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)`['s', 'b', 'B', 'h', 'H', 'i', 'I', 'l', 'L', 'q', 'Q', 'f', 'd'] = 'f'`_, is_big_endian: [bool](https://docs.python.org/3/library/functions.html#bool) = False, termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, header_fmt: [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)`['ieee', 'hp', 'rs', 'empty'] = 'ieee'`_)

Write a string message and append binary-formatted values to the device.

The write_termination is always appended to it.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The header of the message to be sent.

- **values** (Sequence**[**Any\*\*]) – Data to be written to the device.

- **datatype** (util.BINARY_DATATYPES**, **optional) – Format string for one element; see the struct module.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Indicates whether the data use big endian or little endian order.

- **termination** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Character termination override. If None, write_termination supplies the value. Defaults to None.

- **encoding** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Encoding override for converting str to bytes. If None, encoding supplies the value. Defaults to None.

- **header_fmt** (util.BINARY_HEADERS) – Header format that prefixes the data.

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

*class *pyvisa.resources.GPIBInstrument(resource_manager: [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager), resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str))[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/gpib.html#GPIBInstrument)

Communicates with to devices of type GPIB::<primary address>[::INSTR]

More complex resource names can be specified with the following grammar:

GPIB[board]::primary address[::secondary address][::INSTR]

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

Byte count read per operation. Some resources, such as serial resources, may reject large chunk sizes.

clear() → [None](https://docs.python.org/3/library/constants.html#None)

Clear this resource.

close() → [None](https://docs.python.org/3/library/constants.html#None)

Closes the VISA session and marks the handle as invalid.

control_ren(mode: RENLineOperation) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Controls the state of the GPIB Remote Enable (REN) interface line.

The remote/local state of the device can also be controlled optionally.

Corresponds to viGpibControlREN function of the VISA library.

Parameters:

**mode** (constants.RENLineOperation) – Sets the REN line state and, optionally, the device remote/local state.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

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

  enable_repeat_addressing*: Attribute[[bool](https://docs.python.org/3/library/functions.html#bool)]*

Whether to use repeat addressing before each read or write operation.

enable_unaddressing*: Attribute[[bool](https://docs.python.org/3/library/functions.html#bool)]*

Whether the device should be unaddressed with UNT and UNL after each read or write operation.

*property *encoding*: [str](https://docs.python.org/3/library/stdtypes.html#str)*

Encoding used for read and write operations.

flush(mask: BufferOperation) → [None](https://docs.python.org/3/library/constants.html#None)

Manually clears the specified buffers.

Depending on the mask value, this can write buffer data to the device.

Parameters:

**mask** (constants.BufferOperation) – Action used when flushing the buffer. See highlevel.VisaLibraryBase.flush for a detailed description.

get_visa_attribute(name: ResourceAttribute) → [Any](https://docs.python.org/3/library/typing.html#typing.Any)

Retrieves the state of an attribute in this resource.

For frequently used attributes, prefer the dedicated descriptor because it checks values and performs automatic conversion.

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

- **user_handle** – Application-supplied value that uniquely identifies handlers for an event type. Backend restrictions may apply; see the backend install_visa_handler details.

Returns:

User handle in the backend-compatible format. Use this representation when uninstalling a handler.

Return type:

Any

interface_number*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Board number for the given interface.
