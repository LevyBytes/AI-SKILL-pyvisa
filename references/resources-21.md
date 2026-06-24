# Resources (part 21)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

**user_handle** (Any) – The user handle returned by install_handler.

unlock() → [None](https://docs.python.org/3/library/constants.html#None)

Relinquishes a lock for the specified resource.

visa_attributes_classes*: ClassVar[Set[Type[attributes.Attribute]]]\*\* = {<class 'pyvisa.attributes.AttrVI_ATTR_DEST_ACCESS_PRIV'>, <class 'pyvisa.attributes.AttrVI_ATTR_DEST_BYTE_ORDER'>, <class 'pyvisa.attributes.AttrVI_ATTR_DEST_INCREMENT'>, <class 'pyvisa.attributes.AttrVI_ATTR_DMA_ALLOW_EN'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_INST_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_NUM'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_TYPE'>, <class 'pyvisa.attributes.AttrVI_ATTR_MAX_QUEUE_LENGTH'>, <class 'pyvisa.attributes.AttrVI_ATTR_RM_SESSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_CLASS'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_IMPL_VERSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_LOCK_STATE'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_ID'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_SPEC_VERSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_SRC_ACCESS_PRIV'>, <class 'pyvisa.attributes.AttrVI_ATTR_SRC_BYTE_ORDER'>, <class 'pyvisa.attributes.AttrVI_ATTR_SRC_INCREMENT'>, <class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>, <class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>, <class 'pyvisa.attributes.AttrVI_ATTR_VXI_LA'>, <class 'pyvisa.attributes.AttrVI_ATTR_WIN_ACCESS'>, <class 'pyvisa.attributes.AttrVI_ATTR_WIN_ACCESS_PRIV'>, <class 'pyvisa.attributes.AttrVI_ATTR_WIN_BASE_ADDR'>, <class 'pyvisa.attributes.AttrVI_ATTR_WIN_BYTE_ORDER'>, <class 'pyvisa.attributes.AttrVI_ATTR_WIN_SIZE'>}*

VISA attribute descriptor classes let code inspect supported attributes and the values they may accept. Frequently used attributes are usually exposed directly on the resource.

visalib*: [highlevel.VisaLibraryBase](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase)*

Reference to the VISA library instance used by the resource

wait_on_event(in_event_type: EventType, timeout: [int](https://docs.python.org/3/library/functions.html#int), capture_timeout: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → WaitResponse

Waits for an occurrence of the specified event in this resource.

in_event_typeconstants.EventType

Logical identifier of the event(s) to wait for.

timeoutint

Absolute wait duration, in milliseconds, for a specified event before the resource returns the time elapsed error. None allows it to wait indefinitely when needed.

capture_timeoutbool, optional

If True, timeout handling returns a WaitResponse with timed_out=True instead of raising VisaIOError(VI_ERROR_TMO).

Returns:

Object that contains event_type, context and ret value.

Return type:

WaitResponse

wrap_handler(callable: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[Resource, Event, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]) → [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]

Wrap an event handler to provide the signature expected by VISA.

A handler must use this signature: handler(resource: Resource, event: Event, user_handle: Any) -> None.

Use the wrapped handler only for events on the same resource that produced the wrapper.

write_memory(space: AddressSpace, offset: [int](https://docs.python.org/3/library/functions.html#int), data: [int](https://docs.python.org/3/library/functions.html#int), width: DataWidth, extended: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Write a value to the specified memory space and offset.

Parameters:

- **space** (constants.AddressSpace) – Specifies the address space.

- **offset** ([int](https://docs.python.org/3/library/functions.html#int)) - Byte offset for the address or register to read from.

- **data** ([int](https://docs.python.org/3/library/functions.html#int)) – Data to write to bus.

- **width** (Union**[**Literal**[**8**, **16**, **32**, **64**]**, **constants.DataWidth**]) - Bit count for the read operation.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) - Use a 64 bits offset regardless of platform; the default is False.

Returns:

Return value of the library call.

Return type:

[constants.StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Raises:

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError) – Raised if an invalid width is specified.

*class *pyvisa.resources.VXIBackplane(resource_manager: [ResourceManager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager), resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str))[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/resources/vxi.html#VXIBackplane)

Communicates with to devices of type VXI::BACKPLANE

More complex resource names can be specified with the following grammar:

VXI[board][::VXI logical address]::BACKPLANE

Do not instantiate directly, use [`pyvisa.highlevel.ResourceManager.open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource).

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

For often used attributes, prefer the dedicated descriptor; it checks values and converts them automatically.

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

- **user_handle** - Application-provided value used to uniquely identify handlers for an event type. Backends may restrict accepted values; see the backend install_visa_handler details.

Returns:

The user handle is represented in the form expected by the backend. Use that representation when uninstalling a handler.

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

- **timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) - How long, in milliseconds, the resource waits for the locking session to release it before returning an error. The default "default" uses self.timeout.

- **requested_key** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) - Access key from another session for sharing a lock, or None to create a new shared access key.

Returns:

If requested_key is None, returns a new shared access key; otherwise returns requested_key unchanged.

Return type:

[str](https://docs.python.org/3/library/stdtypes.html#str)

lock*context(timeout: [float](https://docs.python.org/3/library/functions.html#float) | [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['default'] = 'default'*, requested*key: [str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None) = 'exclusive'*) → [Iterator](https://docs.python.org/3/library/typing.html#typing.Iterator)[[str](https://docs.python.org/3/library/stdtypes.html#str) | [None](https://docs.python.org/3/library/constants.html#None)]

A context that locks

Parameters:

- **timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) - Time in milliseconds that the resource waits for the locking session to unlock it before an error is returned. The "default" value means self.timeout is used.

- **requested_key** (Optional\*\*[[str](https://docs.python.org/3/library/stdtypes.html#str)]**, **optional) - With the default of 'exclusive', the lock is exclusive. Otherwise, pass the shared-lock access key, or use None to generate a new shared access key.

Yields:

Optional[str] – The access_key if applicable.

lock*excl(timeout: [float](https://docs.python.org/3/library/functions.html#float) | [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)['default'] = 'default'*) → [None](https://docs.python.org/3/library/constants.html#None)

Establish an exclusive lock to the resource.

Parameters:

**timeout** (Union\*\*[[float](https://docs.python.org/3/library/functions.html#float), **Literal**[**"default"**]**]**, \*\*optional) - Milliseconds to wait for the locking session to release the resource before reporting an error. Defaults to "default", which uses self.timeout.

lock_state*: Attribute[[constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes)]*

Current locking state of the resource.

open(access_mode: [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes) = AccessModes.no_lock, open_timeout: [int](https://docs.python.org/3/library/functions.html#int) = 5000) → [None](https://docs.python.org/3/library/constants.html#None)

Opens a session to the specified resource.

Parameters:

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), \*\*optional) - Access mode requested for the resource. Defaults to constants.AccessModes.no_lock.

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) - If `access_mode` requests a lock, this sets how long, in milliseconds, the resource waits to be unlocked before the operation errors. Defaults to 5000.

  *classmethod *register(interface_type: [InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType), resource_class: [str](https://docs.python.org/3/library/stdtypes.html#str)) → [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[[Type](https://docs.python.org/3/library/typing.html#typing.Type)[T]], [Type](https://docs.python.org/3/library/typing.html#typing.Type)[T]]

Create a decorator to register a class.

The class is associated to an interface type, resource class pair.

Parameters:

- **interface_type** ([constants.InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)) – Interface type for which to register a wrapper class.

- **resource_class** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Resource class for which to register a wrapper class.

Returns:

Decorator used to register the class. Raises TypeError when required VISA attributes are absent from the registered class.

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

For attributes used often, the dedicated descriptor is preferred because it validates the value and applies automatic conversion.

Parameters:

- **name** (constants.ResourceAttribute) – Attribute for which the state is to be modified.

- **state** (Any) - State value to assign to the attribute for the specified object.

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

visa_attributes_classes*: ClassVar[Set[Type[attributes.Attribute]]]\*\* = {<class 'pyvisa.attributes.AttrVI_ATTR_INTF_INST_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_NUM'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_PARENT_NUM'>, <class 'pyvisa.attributes.AttrVI_ATTR_INTF_TYPE'>, <class 'pyvisa.attributes.AttrVI_ATTR_MAINFRAME_LA'>, <class 'pyvisa.attributes.AttrVI_ATTR_MAX_QUEUE_LENGTH'>, <class 'pyvisa.attributes.AttrVI_ATTR_RM_SESSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_CLASS'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_IMPL_VERSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_LOCK_STATE'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_ID'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_MANF_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_NAME'>, <class 'pyvisa.attributes.AttrVI_ATTR_RSRC_SPEC_VERSION'>, <class 'pyvisa.attributes.AttrVI_ATTR_TMO_VALUE'>, <class 'pyvisa.attributes.AttrVI_ATTR_TRIG_ID'>, <class 'pyvisa.attributes.AttrVI_ATTR_USER_DATA'>, <class 'pyvisa.attributes.AttrVI_ATTR_VXI_TRIG_STATUS'>, <class 'pyvisa.attributes.AttrVI_ATTR_VXI_TRIG_SUPPORT'>, <class 'pyvisa.attributes.AttrVI_ATTR_VXI_VME_INTR_STATUS'>, <class 'pyvisa.attributes.AttrVI_ATTR_VXI_VME_SYSFAIL_STATE'>}*

VISA attribute descriptor classes provide introspection for supported attributes and their possible values. The attributes used most often are generally available directly on the resource.

visalib*: [highlevel.VisaLibraryBase](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase)*

Reference to the VISA library instance used by the resource

wait_on_event(in_event_type: EventType, timeout: [int](https://docs.python.org/3/library/functions.html#int), capture_timeout: [bool](https://docs.python.org/3/library/functions.html#bool) = False) → WaitResponse

Waits for an occurrence of the specified event in this resource.

in_event_typeconstants.EventType

Logical identifier of the event(s) to wait for.

timeoutint

Absolute period, measured in milliseconds, that the resource waits for a specific event before returning the time elapsed error. None means it can wait forever if required.

capture_timeoutbool, optional

When True, this returns a WaitResponse with timed_out=True for a timeout rather than producing VisaIOError(VI_ERROR_TMO).

Returns:

Object that contains event_type, context and ret value.

Return type:

WaitResponse

wrap_handler(callable: [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[Resource, Event, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]) → [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)[[VISASession, EventType, VISAEventContext, [Any](https://docs.python.org/3/library/typing.html#typing.Any)], [None](https://docs.python.org/3/library/constants.html#None)]

Wrap an event handler to provide the signature expected by VISA.

Use this handler form: handler(resource: Resource, event: Event, user_handle: Any) -> None.

Apply the wrapped handler only to events emitted by the resource that created that wrapper.
