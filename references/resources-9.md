# Resources (part 9)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

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

*class *pyvisa.resources.USBInstrument(resource_manager: [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager), resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str))[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/usb.html#USBInstrument)

USB INSTR resources USB::manufacturer ID::model code::serial number

More complex resource names can be specified with the following grammar:

USB[board]::manufacturer ID::model code::serial number[::USB interface number][::INSTR]

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

control_in(request_type_bitmap_field: [int](https://docs.python.org/3/library/functions.html#int), request_id: [int](https://docs.python.org/3/library/functions.html#int), request_value: [int](https://docs.python.org/3/library/functions.html#int), index: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int) = 0) → [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/usb.html#USBInstrument.control_in)

Performs a USB control pipe transfer from the device.

Parameters:

- **request_type_bitmap_field** ([int](https://docs.python.org/3/library/functions.html#int)) – bmRequestType parameter of the setup stage of a USB control transfer.

- **request_id** ([int](https://docs.python.org/3/library/functions.html#int)) – bRequest parameter of the setup stage of a USB control transfer.

- **request_value** ([int](https://docs.python.org/3/library/functions.html#int)) – wValue parameter of the setup stage of a USB control transfer.

- **index** ([int](https://docs.python.org/3/library/functions.html#int)) – wIndex parameter for the setup stage of a USB control transfer. Usually this is the interface or endpoint index.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) – wLength parameter for the setup stage of a USB control transfer. This also sets the receive buffer size for data from the optional data stage of the control transfer.

Returns:

Data buffer receiving data from the optional data stage of the control transfer.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

control*out(request_type_bitmap_field: [int](https://docs.python.org/3/library/functions.html#int), request_id: [int](https://docs.python.org/3/library/functions.html#int), request_value: [int](https://docs.python.org/3/library/functions.html#int), index: [int](https://docs.python.org/3/library/functions.html#int), data: [bytes](https://docs.python.org/3/library/stdtypes.html#bytes) = b''*)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/usb.html#USBInstrument.control_out)

Performs a USB control pipe transfer to the device.

Parameters:

- **request_type_bitmap_field** ([int](https://docs.python.org/3/library/functions.html#int)) – bmRequestType parameter of the setup stage of a USB control transfer.

- **request_id** ([int](https://docs.python.org/3/library/functions.html#int)) – bRequest parameter of the setup stage of a USB control transfer.

- **request_value** ([int](https://docs.python.org/3/library/functions.html#int)) – wValue parameter of the setup stage of a USB control transfer.

- **index** ([int](https://docs.python.org/3/library/functions.html#int)) – wIndex parameter for the setup stage of a USB control transfer. Usually this is the interface or endpoint index.

- **data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – Data buffer sent during the optional data stage of the control transfer.

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

USB interface number used by the given session.

interface_type*: Attribute[[constants.InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)]*

Interface type of the given session.

io_protocol*: Attribute[[constants.IOProtocol](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.IOProtocol)]*

IO protocol to use. See the attribute definition for more details.

is_4882_compliant*: Attribute[[bool](https://docs.python.org/3/library/functions.html#bool)]*

Whether the device is 488.2 compliant.

*property *last_status*: [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)*

Last status code for this session.

lock(timeout: [float](https://docs.python.org/3/library/functions.html#float) | [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['default'] = 'default'\_, requested_key: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [str](https://docs.python.org/3/library/stdtypes.html#str)

Establish a shared lock to the resource.

Parameters:

- **timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) – Time in milliseconds that the resource waits for the locking session to release it before an error is returned. The default is “default”, which uses self.timeout.

- **requested_key** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Access key from another session for sharing a lock, or None to create a new shared access key.

Returns:

A new shared access key when requested_key is None; otherwise the requested_key value.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

lock*context(timeout: [float](https://docs.python.org/3/library/functions.html#float) | [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['default'] = 'default'*, requested*key: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = 'exclusive'*) → [Iterator](https://docs.python.org/3/library/typing.html#typing.Iterator)[[str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)]

A context that locks

Parameters:

- **timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) – Time in milliseconds that the resource waits for the locking session to release it before an error is returned. The default is “default”, which uses self.timeout.

- **requested_key** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – With the default ‘exclusive’, the session takes an exclusive lock. For a shared lock, pass the access key, or pass None to create a new shared access key.

Yields:

Optional[str] – The access_key if applicable.

lock*excl(timeout: [float](https://docs.python.org/3/library/functions.html#float) | [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['default'] = 'default'*) → [None](https://docs.python.org/3/library/constants.html#None)

Establish an exclusive lock to the resource.

Parameters:

**timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) – Time in milliseconds that the resource waits for the locking session to release it before an error is returned. The default is “default”, which uses self.timeout.

lock_state*: Attribute[[constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes)]*

Current locking state of the resource.

manufacturer_id*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Manufacturer identification number of the device.

manufacturer_name*: Attribute[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

Manufacturer name.

maximum_interrupt_size*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Maximum data size stored for one USB interrupt.

model_code*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Model code for the device.

model_name*: Attribute[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

Model name of the device.

open(access_mode: [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes) = AccessModes.no_lock, open_timeout: [int](https://docs.python.org/3/library/functions.html#int) = 5000) → [None](https://docs.python.org/3/library/constants.html#None)

Opens a session to the specified resource.

Parameters:

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), \*\*optional) – Selects how the resource is accessed. Defaults to constants.AccessModes.no_lock.

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – When the `access_mode` parameter requests a lock, this is the wait in milliseconds for the resource to unlock before the operation errors. Defaults to 5000.

  query(message: [str](https://docs.python.org/3/library/stdtypes.html#str), delay: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [str](https://docs.python.org/3/library/stdtypes.html#str)

A combination of write(message) and read()

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **delay** (Optional\*\*[[float](https://docs.python.org/3/library/functions.html#float)]**, **optional) – Wait time in seconds between the write and read steps. If None, uses self.query_delay.

Returns:

Answer from the device.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

query_ascii_values(message: str, converter=`~typing.Literal['s', 'b', 'c', 'd', 'o', 'x', 'X', 'e', 'E', 'f', 'F', 'g', 'G'] | ~typing.Callable[[str], ~typing.Any] = 'f'`, separator=`str | ~typing.Callable[[str], ~typing.Iterable[str]] = ','`, container=`~typing.Type | ~typing.Callable[[~typing.Iterable], ~typing.Sequence] = <class 'list'>`, delay=`float | None = None`\*) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[Any](https://docs.python.org/3/library/typing.html#typing.Any)]

Query the device and parse returned ASCII values into an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **converter** (ASCII_CONVERTER**, **optional) – Str format of function to convert each value. Default to “f”.

- **separator** (Union\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str), **Callable**[\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **Iterable\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**]**]) – Use a str or callable to divide the returned data into elements. With a str, data.split(separator) is used. Default is “,”.

- **container** (Union**[**Type**, **Callable**[**[**Iterable**]**, **Sequence**]**]**, **optional) – Container type for returned data. Accepted examples include list, tuple, np.ndarray, and similar containers. Default is list.

- **delay** (Optional\*\*[[float](https://docs.python.org/3/library/functions.html#float)]**, **optional) – Wait time in seconds between the write and read steps. If None, uses self.query_delay.

Returns:

Parsed data.

Return type:

Sequence
