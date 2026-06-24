# Resources (part 15)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

pass_control(primary_address: [int](https://docs.python.org/3/library/functions.html#int), secondary_address: [int](https://docs.python.org/3/library/functions.html#int)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/gpib.html#GPIBInterface.pass_control)

Instruct a GPIB device to take over as controller in charge (CIC).

This maps to the VISA library viGpibPassControl function.

Parameters:

- **primary_address** ([int](https://docs.python.org/3/library/functions.html#int)) – Primary address for the GPIB device that should receive control.

- **secondary_address** ([int](https://docs.python.org/3/library/functions.html#int)) – Secondary address for the selected GPIB device. Use Constants.NO_SEC_ADDR when that device has no secondary address.

Returns:

Status returned by the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

primary_address*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Primary address for the GPIB device associated with this session.

query(message: [str](https://docs.python.org/3/library/stdtypes.html#str), delay: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [str](https://docs.python.org/3/library/stdtypes.html#str)

Run write(message), then read(), as one query operation.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Message that will be sent.

- **delay** (Optional\*\*[[float](https://docs.python.org/3/library/functions.html#float)]**, **optional) – Seconds to wait between the write and read steps. With None, self.query_delay is used.

Returns:

Response received from the device.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

query_ascii_values(*message: str,
*converter: ~typing.Literal['s', 'b', 'c', 'd', 'o', 'x',
'X', 'e', 'E', 'f', 'F',
'g', 'G'] | ~typing.Callable[[str], ~typing.Any] = 'f',
*separator: str | ~typing.Callable[[str], ~typing.Iterable[str]] = ',',
*container: ~typing.Type | ~typing.Callable[[~typing.Iterable], ~typing.Sequence] = <class 'list'>,
*delay: float | None = None\*) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[Any](https://docs.python.org/3/library/typing.html#typing.Any)]

Ask the device for ASCII-formatted values and return the parsed values as an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Message that will be sent.

- **converter** (ASCII_CONVERTER**, **optional) – String format code or callable used for each value. The default is “f”.

- **separator** (Union\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str), **Callable**[\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **Iterable\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**]**]) – String or callable used to divide the data into elements. When a str is supplied, parsing uses data.split(separator). The default is “,”.

- **container** (Union**[**Type**, **Callable**[**[**Iterable**]**, **Sequence**]**]**, **optional) – Container type for returned data. Valid choices include list, tuple, np.ndarray, and similar types. The default is list.

- **delay** (Optional\*\*[[float](https://docs.python.org/3/library/functions.html#float)]**, **optional) – Seconds to wait between the write and read steps. With None, self.query_delay is used.

Returns:

Parsed values.

Return type:

Sequence

query_binary_values(*message: str,
*datatype: ~typing.Literal['s', 'b', 'B', 'h', 'H', 'i', 'I', 'l', 'L', 'q', 'Q', 'f', 'd'] = 'f',
*is_big_endian: bool = False,
*container: ~typing.Type | ~typing.Callable[[~typing.Iterable], ~typing.Sequence] = <class 'list'>,
*delay: float | None = None,
*header_fmt: ~typing.Literal['ieee', 'hp', 'rs', 'empty'] = 'ieee',
*expect_termination: bool = True,
*data_points: int = 0,
*chunk_size: int | None = None,
*monitoring_interface: ~pyvisa.resources.messagebased.SupportsUpdate | None = None,
*length_before_block: int | None = None,
*raise_on_late_block: bool = False\*) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[int](https://docs.python.org/3/library/functions.html#int) | [float](https://docs.python.org/3/library/functions.html#float)]

Ask the device for binary-formatted values and return the parsed values as an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Message that will be sent.

- **datatype** (BINARY_DATATYPES**, **optional) – Format string for one element. See the struct module. The default is ‘f’.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Selects big-endian rather than little-endian data order. Defaults to False.

- **container** (Union**[**Type**, **Callable**[**[**Iterable**]**, **Sequence**]**]**, **optional) – Container type for returned data. Valid choices include list, tuple, np.ndarray, and similar types. The default is list.

- **delay** (Optional\*\*[[float](https://docs.python.org/3/library/functions.html#float)]**, **optional) – Seconds to wait between the write and read steps. With None, self.query_delay is used.

- **header_fmt** (util.BINARY_HEADERS**, **optional) – Header format placed before the data. Defaults to ‘ieee’.

- **expect_termination** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – When False, the expected binary block length excludes the final termination character (the read termination). Defaults to True.

- **data_points** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Expected point count in the block. It is used only when the instrument does not provide that count. The value is converted to bytes from datatype. Defaults to 0.

- **chunk_size** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Chunk size for reads from the device. Larger chunks can improve speed for large data transfers.

- **monitoring_interface** (SupportsUpdate Protocol**, **optional) – Progress monitor object whose update() method accepts the byte count already read. See the tqdm documentation for details on that progress bar package.

Returns:

Data returned by the device.

Return type:

Sequence[Union[[int](https://docs.python.org/3/library/functions.html#int), [float](https://docs.python.org/3/library/functions.html#float)]]

query_delay*: [float](https://docs.python.org/3/library/functions.html#float)\*\* = 0.0*

Sleep interval, in s, inserted between the write and read portions of a query.

read(termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [str](https://docs.python.org/3/library/stdtypes.html#str)

Read a text response from the device.

Reading ends when the device stops transmitting, such as by setting the relevant bus lines, or when the termination character sequence is found. Only the final character in the termination sequence actually stops the read, but the full sequence is checked against the end of the message; a mismatch causes a warning.

Parameters:

- **termination** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Alternate termination character to apply. With None, read_termination supplies the value. Defaults to None.

- **encoding** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Alternate encoding for converting bytes to str. With None, encoding supplies the value. Defaults to None.

Returns:

Decoded message read from the instrument.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

read*ascii_values(*converter: ~typing.Literal['s', 'b', 'c', 'd', 'o', 'x',
'X', 'e', 'E', 'f', 'F',
'g', 'G'] | ~typing.Callable[[str], ~typing.Any] = 'f',
*separator: str | ~typing.Callable[[str], ~typing.Iterable[str]] = ',',
container: ~typing.Type | ~typing.Callable[[~typing.Iterable], ~typing.Sequence] = <class 'list'>\*) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)

Read ASCII-formatted values from the device and return the parsed values as an iterable.

Parameters:

**converter** (ASCII_CONVERTER**, **optional) – String format code or callable used for each value. The default is “f”.

separatorUnion[str, Callable[[str], Iterable[str]]]

String or callable used to divide the data into elements. When a str is supplied, parsing uses data.split(separator). The default is “,”.

containerUnion[Type, Callable[[Iterable], Sequence]], optional

Container type for returned data. Valid choices include list, tuple, np.ndarray, and similar types. The default is list.

Returns:

Parsed values.

Return type:

Sequence

read_binary_values(*datatype: ~typing.Literal['s', 'b', 'B', 'h', 'H', 'i', 'I', 'l', 'L', 'q', 'Q', 'f', 'd'] = 'f',
*is_big_endian: bool = False,
*container: ~typing.Type | ~typing.Callable[[~typing.Iterable], ~typing.Sequence] = <class 'list'>,
*header_fmt: ~typing.Literal['ieee', 'hp', 'rs', 'empty'] = 'ieee',
*expect_termination: bool = True,
*data_points: int = -1,
*chunk_size: int | None = None,
*monitoring_interface: ~pyvisa.resources.messagebased.SupportsUpdate | None = None,
*length_before_block: int | None = None,
*raise_on_late_block: bool = False\*) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[int](https://docs.python.org/3/library/functions.html#int) | [float](https://docs.python.org/3/library/functions.html#float)]

Read binary-formatted values from the device and return the parsed values as an iterable.

Parameters:

- **datatype** (BINARY_DATATYPES**, **optional) – Format string for one element. See the struct module. The default is ‘f’.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Selects big-endian rather than little-endian data order. Defaults to False.

- **container** (Union**[**Type**, **Callable**[**[**Iterable**]**, **Sequence**]**]**, **optional) – Container type for returned data. Valid choices include list, tuple, np.ndarray, and similar types. The default is list.

- **header_fmt** (util.BINARY_HEADERS**, **optional) – Header format placed before the data. Defaults to ‘ieee’.

- **expect_termination** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – When False, the expected binary block length excludes the final termination character (the read termination). Defaults to True.

- **data_points** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Expected point count in the block. It is used only when the instrument does not provide that count. The value is converted to bytes from datatype. Defaults to 0.

- **chunk_size** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Chunk size for reads from the device. Larger chunks can improve speed for large data transfers.

- **monitoring_interface** (SupportsUpdate Protocol**, **optional) – Progress monitor object whose update() method accepts the byte count already read. See the tqdm documentation for details on that progress bar package.

Returns:

Data returned by the device.

Return type:

Sequence[Union[[int](https://docs.python.org/3/library/functions.html#int), [float](https://docs.python.org/3/library/functions.html#float)]]

read_bytes(count: [int](https://docs.python.org/3/library/functions.html#int), chunk_size: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None) = None, break_on_termchar: [bool](https://docs.python.org/3/library/functions.html#bool) = False, monitoring_interface: SupportsUpdate | [None](https://docs.python.org/3/library/constants.html#None) = None) → [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

Read a requested byte count from the instrument.

Parameters:

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to read from the instrument.

- **chunk_size** (Optional\*\*[[int](https://docs.python.org/3/library/functions.html#int)]**, **optional) – Chunk size used for the read. If count > chunk_size, multiple low-level operations are performed. Defaults to None, which uses the resource-wide configured value.

- **break_on_termchar** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Controls whether reading stops on a termination character or only at message end. Defaults to False.

- **monitoring_interface** (SupportsUpdate Protocol**, **optional) – Progress monitor object whose update() method accepts the byte count already read. See the tqdm documentation for details on that progress bar package.

Returns:

Bytes returned by the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

read_raw(size: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

Read the raw byte string sent from the instrument to the computer.

Unlike read(), this method leaves termination characters in place.

Parameters:

**size** (Optional\*\*[[int](https://docs.python.org/3/library/functions.html#int)]**, **optional) – Chunk size used for the read. Defaults to None, which uses the resource-wide configured value.

Returns:

Bytes returned by the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

read_stb() → [int](https://docs.python.org/3/library/functions.html#int)

Service request status register value.

*property *read_termination*: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

Read termination character setting.

read_termination_context(new_termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)) → [Iterator](https://docs.python.org/3/library/typing.html#typing.Iterator)

*classmethod *register(interface_type: [InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType), resource_class: [str](https://docs.python.org/3/library/stdtypes.html#str)) → [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[[Type](https://docs.python.org/3/library/typing.html#typing.Type)[T]], [Type](https://docs.python.org/3/library/typing.html#typing.Type)[T]]

Create a class-registration decorator.

The registered class is tied to an interface type and resource class pair.

Parameters:

- **interface_type** ([constants.InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)) – Interface type for the wrapper class registration.

- **resource_class** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Resource class for the wrapper class registration.

Returns:

Decorator that registers the class. It raises TypeError when the registered class lacks required VISA attributes.

Return type:

Callable[[Type[T]], Type[T]]

remote_enabled*: Attribute[[constants.LineState](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.LineState)]*

Current GPIB REN (Remote ENable) interface line state.

resource_class*: Attribute[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

Resource class, such as “INSTR”, from the canonical resource name.

*property *resource_info*: [ResourceInfo](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceInfo)*

Return extended information for this resource.

resource_manager*: [highlevel.ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager)*

Reference to the resource manager used for this resource.

resource_manufacturer_name*: Attribute[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

Vendor manufacturer name for the VISA library implementation.

resource_name*: Attribute[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

Unique resource identifier that follows the address structure.

secondary_address*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Secondary address for the GPIB device associated with this session.

send_command(data: [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[int](https://docs.python.org/3/library/functions.html#int), [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/gpib.html#GPIBInterface.send_command)

Write GPIB command bytes to the bus.

This maps to the VISA library viGpibCommand function.

Parameters:

**data** ([bytes](https://docs.python.org/3/library/stdtypes.html#bytes)) – Command bytes to write.

Returns:

- int – Count of bytes written

- constants.StatusCode – Status returned by the library call.

  send_end*: Attribute[[bool](https://docs.python.org/3/library/functions.html#bool)]*

Whether END should be asserted while transferring the buffer's final byte.

send_ifc() → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/gpib.html#GPIBInterface.send_ifc)

Pulse the interface clear line (IFC) for at least 100 microseconds.

This maps to the VISA library viGpibSendIFC function.

*property *session*: VISASession*

Resource session handle value.

Raises:

**errors.InvalidSession** – Raised when the session is closed.

set_visa_attribute(name: ResourceAttribute, state: [Any](https://docs.python.org/3/library/typing.html#typing.Any)) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Set an attribute state.

Prefer the dedicated descriptor for frequently used attributes because it validates and converts values automatically.

Parameters:

- **name** (constants.ResourceAttribute) – Attribute whose state should be changed.

- **state** (Any) – Attribute state to set on the specified object.

Returns:

Status returned by the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

spec_version*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

VISA specification version implemented by the library.

*property *stb*: [int](https://docs.python.org/3/library/functions.html#int)*

Service request status register value.

timeout*: Attribute[[float](https://docs.python.org/3/library/functions.html#float)]*

Timeout, in milliseconds, for all resource I/O operations.

uninstall_handler(event_type: EventType, handler: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)], user_handle=None) → [None](https://docs.python.org/3/library/constants.html#None)

Remove event handlers from this resource.

Parameters:

- **event_type** (constants.EventType) – Logical identifier for the event.

- **handler** (VISAHandler) – Handler function that the client application wants removed.

- **user_handle** (Any) – User handle that install_handler returned.

  unlock() → [None](https://docs.python.org/3/library/constants.html#None)

Release the lock held for the specified resource.

visa_attributes_classes*: ClassVar[Set[Type[attributes.Attribute]]]\*\* = {<class 'pyvisa.attributes.AttrVI_ATTR_DEV_STATUS_BYTE'>, <class 'pyvisa.attributes.AttrVI_ATTR_DMA_ALLOW_EN'>, <class 'pyvisa.attributes.AttrVI_ATTR_FILE_APPEND_EN'>, <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_ADDR_STATE'>, <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_ATN_STATE'>, <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_CIC_STATE'>, <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_HS488_CBL_LEN'>, <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_NDAC_STATE'>, <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_PRIMARY_ADDR'>, <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_REN_STATE'>, <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_SECONDARY_ADDR'>, <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_SRQ_STATE'>, <class 'pyvisa.attributes.AttrVI_ATTR_GPIB_SYS_CNTRL_STATE'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_INST_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_NUM'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_TYPE'>, <class 'pyvisa.attributes.AttrVI_ATTR_IO_PROT'>, <class 'pyvisa.attributes.AttrVI_ATTR_MAX_QUEUE_LENGTH'>, <class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_OPER_MODE'>, <class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_SIZE'>, <class 'pyvisa.attributes.AttrVI_ATTR_RM_SESSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_CLASS'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_IMPL_VERSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_LOCK_STATE'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_ID'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_SPEC_VERSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_SEND_END_EN'>, <class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR'>, <class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR_EN'>, <class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>, <class 'pyvisa.attributes.AttrVI_ATTR_TRIG_ID'>, <class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>, <class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_OPER_MODE'>, <class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_SIZE'>}*

VISA attribute descriptor classes for inspecting supported attributes and allowed values. Frequently used descriptors are usually exposed directly on the resource.

visalib*: [VisaLibraryBase](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase)*

Present when this is used as a mixin with Resource.

wait_on_event(in_event_type: EventType, timeout: [int](https://docs.python.org/3/library/functions.html#int), capture_timeout: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → WaitResponse

Wait for the specified event to occur on this resource.

in_event_typeconstants.EventType

Logical identifier for the event or events to wait on.

timeoutint

Absolute wait period before the resource reports a time elapsed error for the specified event. The unit is milliseconds. None waits indefinitely when needed.

capture_timeoutbool, optional

When True, a timeout returns a WaitResponse with timed_out=True instead of raising VisaIOError(VI_ERROR_TMO).

Returns:

Object containing event_type, context, and ret values.

Return type:

WaitResponse

wrap_handler(callable: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[Resource, Event, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]) → [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]

Wrap an event handler so it matches the signature expected by VISA.

The handler must use this signature: handler(resource: Resource, event: Event, user_handle: Any) -> None.

Use the wrapped handler only for events on the resource that created the wrapper.
