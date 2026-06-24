# Resources (part 11)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

**values** (Sequence**[**Any\*\*]) – Data to be written to the device.

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

*class *pyvisa.resources.USBRaw(resource_manager: [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager), resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str))[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/usb.html#USBRaw)

USB RAW resources: USB::manufacturer ID::model code::serial number::RAW

More complex resource names can be specified with the following grammar:

USB[board]::manufacturer ID::model code::serial number[::USB interface number]::RAW

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

query_binary_values(message: str, datatype=`~typing.Literal['s', 'b', 'B', 'h', 'H', 'i', 'I', 'l', 'L', 'q', 'Q', 'f', 'd'] = 'f'`, is_big_endian=`bool = False`, container=`~typing.Type | ~typing.Callable[[~typing.Iterable], ~typing.Sequence] = <class 'list'>`, delay=`float | None = None`, header_fmt=`~typing.Literal['ieee', 'hp', 'rs', 'empty'] = 'ieee'`, expect_termination=`bool = True`, data_points=`int = 0`, chunk_size=`int | None = None`, monitoring_interface=`~pyvisa.resources.messagebased.SupportsUpdate | None = None`, length_before_block=`int | None = None`, raise_on_late_block=`bool = False`\*) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[int](https://docs.python.org/3/library/functions.html#int) | [float](https://docs.python.org/3/library/functions.html#float)]

Query the device and parse returned binary values into an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **datatype** (BINARY_DATATYPES**, **optional) – Format string for one element; see the struct module. Default is ‘f’.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Indicates whether the data use big endian or little endian order. Defaults to False.

- **container** (Union**[**Type**, **Callable**[**[**Iterable**]**, **Sequence**]**]**, **optional) – Container type for returned data. Accepted examples include list, tuple, np.ndarray, and similar containers. Default is list.

- **delay** (Optional\*\*[[float](https://docs.python.org/3/library/functions.html#float)]**, **optional) – Wait time in seconds between the write and read steps. If None, uses self.query_delay.

- **header_fmt** (util.BINARY_HEADERS**, **optional) – Header format that prefixes the data. Defaults to ‘ieee’.

- **expect_termination** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – If False, the expected binary block length excludes the final termination character (the read termination). Defaults to True.

- **data_points** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Expected number of points in the block. Use this only when the instrument does not report the value itself; PyVISA converts it to bytes from the datatype. Defaults to 0.

- **chunk_size** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Chunk size used when reading from the device. Larger chunks can improve throughput for large data transfers.

- **monitoring_interface** (SupportsUpdate Protocol**, **optional) – Progress monitor object with update() method accepting the bytes-read count. See the tqdm documentation (a progress bar package) for details.

Returns:

Data read from the device.

Return type:

Sequence[Union[[int](https://docs.python.org/3/library/functions.html#int), [float](https://docs.python.org/3/library/functions.html#float)]]

query_delay*: [float](https://docs.python.org/3/library/functions.html#float)\*\* = 0.0*

Seconds to sleep between the write and read phases of a query.

read(termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [str](https://docs.python.org/3/library/stdtypes.html#str)

Read a string from the device.

Reading ends when the device stops transmitting (for example by setting the relevant bus lines) or when the termination character sequence is found. Only the final character of the termination sequence actually stops the read; the complete sequence is still checked against the end of the read string message, and a warning is emitted if it differs.

Parameters:

- **termination** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Character termination override. If None, read_termination supplies the value. Defaults to None.

- **encoding** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Encoding override for decoding bytes to str. If None, encoding supplies the value. Defaults to None.

Returns:

Message read from the instrument and decoded.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

read_ascii_values(converter=`~typing.Literal['s', 'b', 'c', 'd', 'o', 'x', 'X', 'e', 'E', 'f', 'F', 'g', 'G'] | ~typing.Callable[[str], ~typing.Any] = 'f'`, separator=`str | ~typing.Callable[[str], ~typing.Iterable[str]] = ','`, container=`~typing.Type | ~typing.Callable[[~typing.Iterable], ~typing.Sequence] = <class 'list'>`) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)

Read ASCII values from the device and return them as an iterable.

Parameters:

**converter** (ASCII_CONVERTER**, **optional) – Str format of function to convert each value. Default to “f”.

separatorUnion[str, Callable[[str], Iterable[str]]]

Use a str or callable to divide the returned data into elements. With a str, data.split(separator) is used. Default is “,”.

containerUnion[Type, Callable[[Iterable], Sequence]], optional

Container type for returned data. Accepted examples include list, tuple, np.ndarray, and similar containers. Default is list.

Returns:

Parsed data.

Return type:

Sequence

read_binary_values(datatype=`~typing.Literal['s', 'b', 'B', 'h', 'H', 'i', 'I', 'l', 'L', 'q', 'Q', 'f', 'd'] = 'f'`, is_big_endian=`bool = False`, container=`~typing.Type | ~typing.Callable[[~typing.Iterable], ~typing.Sequence] = <class 'list'>`, header_fmt=`~typing.Literal['ieee', 'hp', 'rs', 'empty'] = 'ieee'`, expect_termination=`bool = True`, data_points=`int = -1`, chunk_size=`int | None = None`, monitoring_interface=`~pyvisa.resources.messagebased.SupportsUpdate | None = None`, length_before_block=`int | None = None`, raise_on_late_block=`bool = False`) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[int](https://docs.python.org/3/library/functions.html#int) | [float](https://docs.python.org/3/library/functions.html#float)]

Read binary values from the device and return them as an iterable.

Parameters:

- **datatype** (BINARY_DATATYPES**, **optional) – Format string for one element; see the struct module. Default is ‘f’.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Indicates whether the data use big endian or little endian order. Defaults to False.

- **container** (Union**[**Type**, **Callable**[**[**Iterable**]**, **Sequence**]**]**, **optional) – Container type for returned data. Accepted examples include list, tuple, np.ndarray, and similar containers. Default is list.

- **header_fmt** (util.BINARY_HEADERS**, **optional) – Header format that prefixes the data. Defaults to ‘ieee’.

- **expect_termination** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – If False, the expected binary block length excludes the final termination character (the read termination). Defaults to True.

- **data_points** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Expected number of points in the block. Use this only when the instrument does not report the value itself; PyVISA converts it to bytes from the datatype. Defaults to 0.

- **chunk_size** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) – Chunk size used when reading from the device. Larger chunks can improve throughput for large data transfers.

- **monitoring_interface** (SupportsUpdate Protocol**, **optional) – Progress monitor object with update() method accepting the bytes-read count. See the tqdm documentation (a progress bar package) for details.

Returns:

Data read from the device.

Return type:

Sequence[Union[[int](https://docs.python.org/3/library/functions.html#int), [float](https://docs.python.org/3/library/functions.html#float)]]

read_bytes(count: [int](https://docs.python.org/3/library/functions.html#int), chunk_size: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None) = None, break_on_termchar: [bool](https://docs.python.org/3/library/functions.html#bool) = False, monitoring_interface: SupportsUpdate | [None](https://docs.python.org/3/library/constants.html#None) = None) → [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

Read a certain number of bytes from the instrument.

Parameters:

- **count** ([int](https://docs.python.org/3/library/functions.html#int)) – Number of bytes to read from the instrument.

- **chunk_size** (Optional\*\*[[int](https://docs.python.org/3/library/functions.html#int)]**, **optional) – Chunk size used for reading. If count > chunk_size, PyVISA performs multiple low-level operations. Defaults to None, meaning the resource-wide setting is used.

-
