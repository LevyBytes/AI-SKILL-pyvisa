# Resources (part 20)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

visa_attributes_classes*: ClassVar[Set[Type[attributes.Attribute]]]\*\* contains {`<class 'pyvisa.attributes.AttrVI_ATTR_4882_COMPLIANT'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_CMDR_LA'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_DEST_ACCESS_PRIV'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_DEST_BYTE_ORDER'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_DEST_INCREMENT'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_DMA_ALLOW_EN'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_FDC_CHNL'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_FDC_GEN_SIGNAL_EN'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_FDC_MODE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_FDC_USE_PAIR'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_FILE_APPEND_EN'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_IMMEDIATE_SERV'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_INTF_INST_NAME'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_INTF_NUM'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_INTF_TYPE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_IO_PROT'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_MAINFRAME_LA'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_MANF_ID'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_MANF_NAME'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_MAX_QUEUE_LENGTH'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_MEM_BASE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_MEM_SIZE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_MEM_SPACE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_MODEL_CODE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_MODEL_NAME'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_OPER_MODE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_RD_BUF_SIZE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_RM_SESSION'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_RSRC_CLASS'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_RSRC_IMPL_VERSION'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_RSRC_LOCK_STATE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_ID'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_NAME'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_RSRC_NAME'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_RSRC_SPEC_VERSION'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_SEND_END_EN'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_SLOT'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_SRC_ACCESS_PRIV'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_SRC_BYTE_ORDER'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_SRC_INCREMENT'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_SUPPRESS_END_EN'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_TERMCHAR_EN'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_TRIG_ID'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_VXI_DEV_CLASS'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_VXI_LA'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_VXI_TRIG_DIR'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_VXI_TRIG_LINES_EN'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_VXI_TRIG_SUPPORT'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_WIN_ACCESS'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_WIN_ACCESS_PRIV'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_WIN_BASE_ADDR'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_WIN_BYTE_ORDER'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_WIN_SIZE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_OPER_MODE'>`, `<class 'pyvisa.attributes.AttrVI_ATTR_WR_BUF_SIZE'>`}*

VISA attribute descriptor classes expose supported attributes and their valid values for introspection. Commonly used attributes are usually available directly on the resource.

visalib*: [highlevel.VisaLibraryBase](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase)*

Reference to the VISA library instance used by the resource

wait_on_event(in_event_type: EventType, timeout: [int](https://docs.python.org/3/library/functions.html#int), capture_timeout: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → WaitResponse

Waits for an occurrence of the specified event in this resource.

in_event_typeconstants.EventType

Logical identifier of the event(s) to wait for.

timeoutint

Absolute wait interval, in milliseconds, that the resource uses for the specified event before it returns the time elapsed error. None makes the wait indefinite when required.

capture_timeoutbool, optional

When True, return a WaitResponse with timed_out=True instead of raising VisaIOError(VI_ERROR_TMO).

Returns:

Object that contains event_type, context and ret value.

Return type:

WaitResponse

wrap_handler(callable: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[Resource, Event, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]) → [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]

Wrap an event handler to provide the signature expected by VISA.

Handlers must use this signature: handler(resource: Resource, event: Event, user_handle: Any) -> None.

Use the wrapped handler only for events from the same resource that created the wrapper.

write_memory(space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), data: [int](https://docs.python.org/3/library/functions.html#int), width: DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Write a value to the specified memory space and offset.

Parameters:

- **space** (constants.AddressSpace) – Specifies the address space.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) - Byte offset of the address or register read position.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) - Bit width to read.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) - Request 64 bits offset behavior regardless of platform; by default False.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

*class *pyvisa.resources.VXIMemory(resource_manager: [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager), resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str))[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/vxi.html#VXIMemory)

Communicates with to devices of type VXI[board]::MEMACC

More complex resource names can be specified with the following grammar:

VXI[board]::MEMACC

Do not instantiate directly, use [`pyvisa.highlevel.ResourceManager.open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource).

allow_dma*: Attribute[[bool](https://docs.python.org/3/library/functions.html#bool)]*

Should I/O accesses use DMA (True) or Programmed I/O (False).

before_close() → [None](https://docs.python.org/3/library/constants.html#None)

Called just before closing an instrument.

clear() → [None](https://docs.python.org/3/library/constants.html#None)

Clear this resource.

close() → [None](https://docs.python.org/3/library/constants.html#None)

Closes the VISA session and marks the handle as invalid.

destination_increment*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Destination offset increment, in elements, applied after each transfer.

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

For attributes used often, prefer the dedicated descriptor; it validates values and applies automatic conversion.

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

- **user_handle** - Application-supplied value used to uniquely identify handlers for one event type. Some backends restrict which values are accepted; see the backend install_visa_handler for details.

Returns:

Backend-compatible representation of the user handle. Use this representation when uninstalling a handler.

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

- **timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) - Absolute wait, in milliseconds, before an error is returned while a resource is blocked by the locking session. Defaults to "default", which uses self.timeout.

- **requested_key** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) - Access key from another session for sharing its lock, or None to create a new shared access key.

Returns:

If requested_key is None, returns a new shared access key; otherwise returns requested_key unchanged.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

lock*context(timeout: [float](https://docs.python.org/3/library/functions.html#float) | [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['default'] = 'default'*, requested*key: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = 'exclusive'*) → [Iterator](https://docs.python.org/3/library/typing.html#typing.Iterator)[[str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)]

A context that locks

Parameters:

- **timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) - Millisecond timeout for waiting until the locking session unlocks the resource; an error is returned when it expires. The default "default" uses self.timeout.

- **requested_key** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) - With the default 'exclusive', the lock is exclusive. Any other value is used as the shared-lock access key, while None creates a new shared access key.

Yields:

Optional[str] – The access_key if applicable.

lock*excl(timeout: [float](https://docs.python.org/3/library/functions.html#float) | [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['default'] = 'default'*) → [None](https://docs.python.org/3/library/constants.html#None)

Establish an exclusive lock to the resource.

Parameters:

**timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) - Wait duration in milliseconds for the resource to be released by the locking session before returning an error. Defaults to "default", meaning self.timeout is used.

lock_state*: Attribute[[constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes)]*

Current locking state of the resource.

move_in(space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), width: DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [List](https://docs.python.org/3/library/typing.html#typing.List)[[int](https://docs.python.org/3/library/functions.html#int)]

Transfer a data block from the specified address space and offset into local memory.

Corresponds to viMoveIn\* functions of the VISA library.

Parameters:

- **space** (constants.AddressSpace) – Address space from which to move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) - Byte offset of the address or register that supplies the data.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) - Number of elements to transfer; each element uses the same data width as the source.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) - Bits read for each element.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) - Use platform-independent 64 bits offset behavior; by default False.

Returns:

- **data** (List[int]) – Data read from the bus

- **status_code** (constants.StatusCode) – Return value of the library call.

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

move_out(space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), length: [int](https://docs.python.org/3/library/functions.html#int), data: [Iterable](https://docs.python.org/3/library/typing.html#typing.Iterable)[[int](https://docs.python.org/3/library/functions.html#int)], width: DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Transfer a data block from local memory into the specified address space and offset.

Corresponds to viMoveOut\* functions of the VISA library.

Parameters:

- **space** (constants.AddressSpace) – Address space into which move the data.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) - Offset, measured in bytes, for the address or register targeted by the read operation.

- **length** ([int](https://docs.python.org/3/library/functions.html#int)) - Element count for the transfer; each element uses the same data width as the source.

- **data** (Iterable\*\*[[int](https://docs.python.org/3/library/functions.html#int)]) – Data to write to bus.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) - Bit count for each element.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) - When enabled, uses a 64 bits offset without regard to platform; default is False.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

open(access_mode: [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes) = AccessModes.no_lock, open_timeout: [int](https://docs.python.org/3/library/functions.html#int) = 5000) → [None](https://docs.python.org/3/library/constants.html#None)

Opens a session to the specified resource.

Parameters:

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), \*\*optional) - Defines how the resource will be opened. Defaults to constants.AccessModes.no_lock.

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) - When `access_mode` asks for a lock, this value is the wait time, in milliseconds, for the resource to unlock before an error is returned. Defaults to 5000.

  read_memory(space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), width: DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [int](https://docs.python.org/3/library/functions.html#int)

Read a value from the specified memory space and offset.

Parameters:

- **space** (constants.AddressSpace) – Specifies the address space from which to read.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) - Byte offset for the address or register used by the read.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) – Number of bits to read (8, 16, 32 or 64).

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) – Use 64 bits offset independent of the platform.

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

- **interface_type** ([constants.InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)) – Interface type for which to register a wrapper class.

- **resource_class** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Resource class for which to register a wrapper class.

Returns:

Class-registration decorator. It raises TypeError when the registered class lacks required VISA attributes.

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

Prefer the dedicated descriptor for frequently used attributes, because it validates values and performs automatic conversion.

Parameters:

- **name** (constants.ResourceAttribute) – Attribute for which the state is to be modified.

- **state** (Any) - Value to assign as the attribute state on the specified object.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

source_increment*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Element count used to advance the source offset after each transfer.

spec_version*: Attribute[[int](https://docs.python.org/3/library/functions.html#int)]*

Version of the VISA specification to which the implementation is compliant.

timeout*: Attribute[[float](https://docs.python.org/3/library/functions.html#float)]*

Timeout in milliseconds for all resource I/O operations.

uninstall_handler(event_type: EventType, handler: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)], user_handle=None) → [None](https://docs.python.org/3/library/constants.html#None)

Uninstalls handlers for events in this resource.

Parameters:

- **event_type** (constants.EventType) – Logical event identifier.

- **handler** (VISAHandler) – Handler function to be uninstalled by a client application.

-
