# Resources (part 2)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

interface_number*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Board number for the given interface.

interface_type*: Attribute[[constants.InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)]*

Interface type of the given session.

io_protocol*: Attribute[[IOProtocol](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.IOProtocol)]*

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

  query(message: [str](https://docs.python.org/3/library/stdtypes.html#str), delay: [float](https://docs.python.org/3/library/functions.html#float) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [str](https://docs.python.org/3/library/stdtypes.html#str)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.query)

A combination of write(message) and read()

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **delay** (Optional\*\*[[float](https://docs.python.org/3/library/functions.html#float)]**, **optional) – Seconds to pause between the write phase and the read phase. None uses self.query_delay.

Returns:

Answer from the device.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

query_ascii_values(message: str, <wbr>converter: ~typing.Literal['s', <wbr>'b', <wbr>'c', <wbr>'d', <wbr>'o', <wbr>'x', <wbr>'X', <wbr>'e', <wbr>'E', <wbr>'f', <wbr>'F', <wbr>'g', <wbr>'G'] | ~typing.Callable[[str], <wbr>~typing.Any] = 'f', <wbr>separator: str | ~typing.Callable[[str], <wbr>~typing.Iterable[str]] = ',', <wbr>container: ~typing.Type | ~typing.Callable[[~typing.Iterable], <wbr>~typing.Sequence] = <class 'list'>, <wbr>delay: float | None = None) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[Any](https://docs.python.org/3/library/typing.html#typing.Any)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.query_ascii_values)

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

query_binary_values(message: str, <wbr>datatype: ~typing.Literal['s', <wbr>'b', <wbr>'B', <wbr>'h', <wbr>'H', <wbr>'i', <wbr>'I', <wbr>'l', <wbr>'L', <wbr>'q', <wbr>'Q', <wbr>'f', <wbr>'d'] = 'f', <wbr>is_big_endian: bool = False, <wbr>container: ~typing.Type | ~typing.Callable[[~typing.Iterable], <wbr>~typing.Sequence] = <class 'list'>, <wbr>delay: float | None = None, <wbr>header_fmt: ~typing.Literal['ieee', <wbr>'hp', <wbr>'rs', <wbr>'empty'] = 'ieee', <wbr>expect_termination: bool = True, <wbr>data_points: int = 0, <wbr>chunk_size: int | None = None, <wbr>monitoring_interface: ~pyvisa.resources.messagebased.SupportsUpdate | None = None, <wbr>length_before_block: int | None = None, <wbr>raise_on_late_block: bool = False) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[int](https://docs.python.org/3/library/functions.html#int) | [float](https://docs.python.org/3/library/functions.html#float)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.query_binary_values)

Query the device and return parsed binary-format values as an iterable.

Parameters:

- **message** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – The message to send.

- **datatype** (BINARY_DATATYPES**, **optional) – Single-element format string; see the struct module. The default is f.

- **is_big_endian** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Are the data in big or little endian order. Defaults to False.

- **container** (Union**[**Type**, **Callable**[**[**Iterable**]**, **Sequence**]**]**, **optional) – Container used for the parsed output, such as list, tuple, or np.ndarray. The default container is list.

- **delay** (Optional\*\*[[float](https://docs.python.org/3/library/functions.html#float)]**, **optional) – Seconds to pause between the write phase and the read phase. None uses self.query_delay.

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

read(termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None, encoding: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [str](https://docs.python.org/3/library/stdtypes.html#str)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.read)

Read a string from the device.

Reading ends when the device stops sending, such as by setting the relevant bus lines, or when the termination-character sequence is detected. Only the final termination character controls the stop condition, but PyVISA still compares the complete sequence with the end of the read string message and warns if they differ.

Parameters:

- **termination** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Optional termination override. None falls back to read_termination, and the default is None.

- **encoding** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) – Optional decoding override for converting bytes to str. None uses encoding, and the default is None.

Returns:

Message read from the instrument and decoded.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

read*ascii_values(converter: ~typing.Literal['s', <wbr>'b', <wbr>'c', <wbr>'d', <wbr>'o', <wbr>'x', <wbr>'X', <wbr>'e', <wbr>'E', <wbr>'f', <wbr>'F', <wbr>'g', <wbr>'G'] | ~typing.Callable[[str], <wbr>~typing.Any] = 'f', <wbr>separator: str | ~typing.Callable[[str], <wbr>~typing.Iterable[str]] = ',', <wbr>container: ~typing.Type | ~typing.Callable[[~typing.Iterable], <wbr>~typing.Sequence] = <class 'list'>*) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.read_ascii_values)

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

read_binary_values(datatype: ~typing.Literal['s', <wbr>'b', <wbr>'B', <wbr>'h', <wbr>'H', <wbr>'i', <wbr>'I', <wbr>'l', <wbr>'L', <wbr>'q', <wbr>'Q', <wbr>'f', <wbr>'d'] = 'f', <wbr>is_big_endian: bool = False, <wbr>container: ~typing.Type | ~typing.Callable[[~typing.Iterable], <wbr>~typing.Sequence] = <class 'list'>, <wbr>header_fmt: ~typing.Literal['ieee', <wbr>'hp', <wbr>'rs', <wbr>'empty'] = 'ieee', <wbr>expect_termination: bool = True, <wbr>data_points: int = -1, <wbr>chunk_size: int | None = None, <wbr>monitoring_interface: ~pyvisa.resources.messagebased.SupportsUpdate | None = None, <wbr>length_before_block: int | None = None, <wbr>raise_on_late_block: bool = False) → [Sequence](https://docs.python.org/3/library/typing.html#typing.Sequence)[[int](https://docs.python.org/3/library/functions.html#int) | [float](https://docs.python.org/3/library/functions.html#float)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.read_binary_values)

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

read_bytes(count: [int](https://docs.python.org/3/library/functions.html#int), chunk_size: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None) = None, break_on_termchar: [bool](https://docs.python.org/3/library/functions.html#bool) = False, monitoring_interface: SupportsUpdate | [None](https://docs.python.org/3/library/constants.html#None) = None) → [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.read_bytes)

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

read_raw(size: [int](https://docs.python.org/3/library/functions.html#int) | [None](https://docs.python.org/3/library/constants.html#None) = None) → [bytes](https://docs.python.org/3/library/stdtypes.html#bytes)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.read_raw)

Read the unmodified string sent from the instrument to the computer.

In contrast to read(), no termination characters are stripped.

Parameters:

**size** (Optional\*\*[[int](https://docs.python.org/3/library/functions.html#int)]**, **optional) – Chunk size for this read operation. None means the resource-wide value is used.

Returns:

Bytes read from the instrument.

Return type:

[bytes](https://docs.python.org/3/library/stdtypes.html#bytes)

read_stb() → [int](https://docs.python.org/3/library/functions.html#int)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.read_stb)

Service request status register.

*property *read_termination*: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)*

Read termination character.

read_termination_context(new_termination: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)) → [Iterator](https://docs.python.org/3/library/typing.html#typing.Iterator)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/messagebased.html#MessageBasedResource.read_termination_context)

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
