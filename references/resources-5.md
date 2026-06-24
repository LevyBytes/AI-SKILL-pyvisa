# Resources (part 5)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

**delay** (Optional\*\*[[float](https://docs.python.org/3/library/functions.html#float)]**, **optional) – Seconds to pause between the write phase and the read phase. None uses self.query_delay.

- **header_fmt** (util.BINARY_HEADERS**, **optional) – Format of the header prefixing the data. Defaults to ‘ieee’.

- **expect_termination** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – False means the calculated binary block length omits the final termination character, which is the read termination. Defaults to True.

- **data_points** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Expected point count for blocks whose instrument does not provide one. The value is converted to bytes from the datatype. Defaults to 0.

- **chunk_size** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Chunk size used while reading from the device; larger chunks can improve throughput for large data transfers.

- **monitoring_interface** (SupportsUpdate Protocol**, **optional) – Progress monitor whose update() method receives the number of bytes read. The tqdm documentation describes a compatible progress-bar package.

Returns:

Data read from the device.

Return type:

Sequence[Union[[int](https://docs.python.org/3/library/functions.html#int), [float](https://docs.python.org/3/library/functions.html#float)]]

query_delay*: [float](https://docs.python.org/3/library/functions.html#float)\*\* = 0.0*

Sleep interval, in s, inserted between the write and read steps of a query.

read(termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [str](https://docs.python.org/3/library/stdtypes.html#str)

Read a string from the device.

Reading ends when the device stops sending, such as by setting the relevant bus lines, or when the termination-character sequence is detected. Only the final termination character controls the stop condition, but PyVISA still compares the complete sequence with the end of the read string message and warns if they differ.

Parameters:

- **termination** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Optional termination override. None falls back to read_termination, and the default is None.

- **encoding** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Optional decoding override for converting bytes to str. None uses encoding, and the default is None.

Returns:

Message read from the instrument and decoded.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

read*ascii_values(converter: ~typing.Literal['s', <wbr>'b', <wbr>'c', <wbr>'d', <wbr>'o', <wbr>'x', <wbr>'X', <wbr>'e', <wbr>'E', <wbr>'f', <wbr>'F', <wbr>'g', <wbr>'G'] | ~typing.Callable[[str], <wbr>~typing.Any] = 'f', <wbr>separator: str | ~typing.Callable[[str], <wbr>~typing.Iterable[str]] = ',', <wbr>container: ~typing.Type | ~typing.Callable[[~typing.Iterable], <wbr>~typing.Sequence] = <class 'list'>*) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)

Read ASCII-format values from the device and return them as an iterable.

Parameters:

**converter** (ASCII_CONVERTER**, **optional) – String format code or callable used to convert each value. Defaults to f.

separatorUnion[str, Callable[[str], Iterable[str]]]

Separator policy for splitting returned data into individual elements. A str calls data.split(separator); the default is comma.

containerUnion[Type, Callable[[Iterable], Sequence]], optional

Container used for the parsed output, such as list, tuple, or np.ndarray. The default container is list.

Returns:

Parsed data.

Return type:

Sequence

read_binary_values(datatype: ~typing.Literal['s', <wbr>'b', <wbr>'B', <wbr>'h', <wbr>'H', <wbr>'i', <wbr>'I', <wbr>'l', <wbr>'L', <wbr>'q', <wbr>'Q', <wbr>'f', <wbr>'d'] = 'f', <wbr>is_big_endian: bool = False, <wbr>container: ~typing.Type | ~typing.Callable[[~typing.Iterable], <wbr>~typing.Sequence] = <class 'list'>, <wbr>header_fmt: ~typing.Literal['ieee', <wbr>'hp', <wbr>'rs', <wbr>'empty'] = 'ieee', <wbr>expect_termination: bool = True, <wbr>data_points: int = -1, <wbr>chunk_size: int | None = None, <wbr>monitoring_interface: ~pyvisa.resources.messagebased.SupportsUpdate | None = None, <wbr>length_before_block: int | None = None, <wbr>raise_on_late_block: bool = False) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[int](https://docs.python.org/3/library/functions.html#int) | [float](https://docs.python.org/3/library/functions.html#float)]

Read binary-format values from the device and return them as an iterable.

Parameters:

- **datatype** (BINARY_DATATYPES**, **optional) – Single-element format string; see the struct module. The default is f.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Are the data in big or little endian order. Defaults to False.

- **container** (Union**[**Type**, **Callable**[**[**Iterable**]**, **Sequence**]**]**, **optional) – Container used for the parsed output, such as list, tuple, or np.ndarray. The default container is list.

- **header_fmt** (util.BINARY_HEADERS**, **optional) – Format of the header prefixing the data. Defaults to ‘ieee’.

- **expect_termination** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – False means the calculated binary block length omits the final termination character, which is the read termination. Defaults to True.

- **data_points** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Expected point count for blocks whose instrument does not provide one. The value is converted to bytes from the datatype. Defaults to 0.

- **chunk_size** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Chunk size used while reading from the device; larger chunks can improve throughput for large data transfers.

- **monitoring_interface** (SupportsUpdate Protocol**, **optional) – Progress monitor whose update() method receives the number of bytes read. The tqdm documentation describes a compatible progress-bar package.

Returns:

Data read from the device.

Return type:

Sequence[Union[[int](https://docs.python.org/3/library/functions.html#int), [float](https://docs.python.org/3/library/functions.html#float)]]

read_bytes(count: [int](https://docs.python.org/3/library/functions.html#int), chunk_size: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None) = None, break_on_termchar: [bool](https://docs.python.org/3/library/functions.html#bool) = False, monitoring_interface: SupportsUpdate | [None](https://docs.python.org/3/library/constants.html#None) = None) → [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

Read a certain number of bytes from the instrument.

Parameters:

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – The number of bytes to read from the instrument.

- **chunk_size** (Optional\*\*[[int](https://docs.python.org/3/library/functions.html#int)]**, **optional) – Chunk size for this read operation. If count > chunk_size, several low-level reads are used. None means the resource-wide value is used.

- **break_on_termchar** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Controls whether reading stops at a termination character instead of waiting for the message end. Defaults to False.

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

replace_char*: Attribute[[str](https://docs.python.org/3/library/stdtypes.html#str)]*

Replacement character for incoming characters received with errors. The default character is 0.

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

stop_bits*: Attribute[[StopBits](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StopBits)]*

Stop-bit count that marks the end of a frame. The default is constants.StopBits.one (VI_ASRL_STOP_ONE).

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

visa_attributes_classes*: ClassVar[Set[Type[attributes.Attribute]]]\*\* = {<class 'pyvisa.attributes.AttrVI_ATTR_ASRL_ALLOW_TRANSMIT'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_AVAIL_NUM'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_BAUD'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_BREAK_LEN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_BREAK_STATE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_CONNECTED'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_CTS_STATE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_DATA_BITS'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_DCD_STATE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_DISCARD_NULL'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_DSR_STATE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_DTR_STATE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_END_IN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_END_OUT'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_FLOW_CNTRL'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_PARITY'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_REPLACE_CHAR'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_RI_STATE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_RTS_STATE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_STOP_BITS'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_WIRE_MODE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_XOFF_CHAR'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_ASRL_XON_CHAR'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_DMA_ALLOW_EN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_FILE_APPEND_EN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_INTF_INST_NAME'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_INTF_NUM'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_INTF_TYPE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_IO_PROT'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_MAX_QUEUE_LENGTH'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_OPER_MODE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_SIZE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RM_SESSION'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_CLASS'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_IMPL_VERSION'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_LOCK_STATE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_ID'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_NAME'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_NAME'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_RSRC_SPEC_VERSION'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_SEND_END_EN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_SUPPRESS_END_EN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR_EN'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_TRIG_ID'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_OPER_MODE'>, <wbr><class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_SIZE'>}*

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

-
