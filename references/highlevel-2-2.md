# Highlevel (part 2) (2)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def buffer_read(self, session: VISASession, count: int) -> Tuple[bytes, StatusCode]:
"""Reads data through the use of a formatted I/O read buffer.

        The data can be read from a device or an interface.

        Corresponds to viBufRead function of the VISA library.

        Parameters
        ----------
        session : VISASession\
            Unique logical identifier to a session.
        count : int
            Number of bytes to be read.

        Returns
        -------
        dbytes
            Data read
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def buffer_write(self, session: VISASession, data: bytes) -> Tuple[int, StatusCode]:
"""Writes data to a formatted I/O write buffer synchronously.

        Corresponds to viBufWrite function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        data : bytes
            Data to be written.

        Returns
        -------
        int
            number of written bytes
        StatusCode
            return value of the library call.

        """
        raise NotImplementedError

[docs]
def clear(self, session: VISASession) -> StatusCode:
"""Clears a device.

        Corresponds to viClear function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def close(
self, session: Union[VISASession, VISAEventContext, VISARMSession]
) -> StatusCode:
"""Closes the specified session, event, or find list.

        Corresponds to viClose function of the VISA library.

        Parameters
        ---------
        session : Union[VISASession, VISAEventContext, VISARMSession]
            Unique logical identifier to a session, event, resource manager.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def disable_event(
self,
session: VISASession,
event_type: constants.EventType,
mechanism: constants.EventMechanism,
) -> StatusCode:
"""Disable notification for an event type(s) via the specified mechanism(s).

        Corresponds to viDisableEvent function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Event type.
        mechanism : constants.EventMechanism
            Event handling mechanisms to be disabled.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def discard_events(
self,
session: VISASession,
event_type: constants.EventType,
mechanism: constants.EventMechanism,
) -> StatusCode:
"""Discard event occurrences for a given type and mechanisms in a session.

        Corresponds to viDiscardEvents function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Logical event identifier.
        mechanism : constants.EventMechanism
            Specifies event handling mechanisms to be discarded.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def enable_event(
self,
session: VISASession,
event_type: constants.EventType,
mechanism: constants.EventMechanism,
context: None = None,
) -> StatusCode:
"""Enable event occurrences for specified event types and mechanisms in a session.

        Corresponds to viEnableEvent function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Logical event identifier.
        mechanism : constants.EventMechanism
            Specifies event handling mechanisms to be enabled.
        context : None, optional
            Unused parameter...

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def flush(
self, session: VISASession, mask: constants.BufferOperation
) -> StatusCode:
"""Flush the specified buffers.

        The buffers can be associated with formatted I/O operations and/or
        serial communication.

        Corresponds to viFlush function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        mask : constants.BufferOperation
            Specifies the action to be taken with flushing the buffer.
            The values can be combined using the | operator. However multiple
            operations on a single buffer cannot be combined.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def get_attribute(
self,
session: Union[VISASession, VISAEventContext, VISARMSession],
attribute: Union[constants.ResourceAttribute, constants.EventAttribute],
) -> Tuple[Any, StatusCode]:
"""Retrieves the state of an attribute.

        Corresponds to viGetAttribute function of the VISA library.

        Parameters
        ----------
        session : Union[VISASession, VISAEventContext]
            Unique logical identifier to a session, event, or find list.
        attribute : Union[constants.ResourceAttribute, constants.EventAttribute]
            Resource or event attribute for which the state query is made.

        Returns
        -------
        Any
            State of the queried attribute for a specified resource
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def gpib_command(self, session: VISASession, data: bytes) -> Tuple[int, StatusCode]:
"""Write GPIB command bytes on the bus.

        Corresponds to viGpibCommand function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        data : bytes
            Data to write.

        Returns
        -------
        int
            Number of written bytes
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def gpib_control_atn(
self, session: VISASession, mode: constants.ATNLineOperation
) -> StatusCode:
"""Controls the ATN line state and whether the local interface acts as active controller.

        Corresponds to viGpibControlATN function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        mode : constants.ATNLineOperation
            State of the ATN line and optionally the local active controller state.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def gpib_control_ren(
self, session: VISASession, mode: constants.RENLineOperation
) -> StatusCode:
"""Controls the state of the GPIB Remote Enable (REN) interface line.

        Optionally the remote/local state of the device can also be set.

        Corresponds to viGpibControlREN function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        mode : constants.RENLineOperation
            State of the REN line and optionally the device remote/local state.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def gpib_pass_control(
self, session: VISASession, primary_address: int, secondary_address: int
) -> StatusCode:
"""Tell a GPIB device to become controller in charge (CIC).

        Corresponds to viGpibPassControl function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        primary_address : int
            Primary address for the GPIB device that will receive control.
        secondary_address : int
            Secondary address of the targeted GPIB device.
            If the targeted device does not have a secondary address, this parameter
            should contain the value Constants.VI_NO_SEC_ADDR.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def gpib_send_ifc(self, session: VISASession) -> StatusCode:
"""Pulse the interface clear line (IFC) for at least 100 microseconds.

        Corresponds to viGpibSendIFC function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def in_8(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
extended: bool = False,
) -> Tuple[int, StatusCode]:
"""Reads an 8-bit value at the given offset within the selected memory space.

        Corresponds to viIn8* function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Specifies the address space.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        extended : bool, optional
            Use 64 bits offset independent of the platform, False by default.

        Returns
        -------
        int
            Data read from memory
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def in_16(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
extended: bool = False,
) -> Tuple[int, StatusCode]:
"""Reads a 16-bit value at the given offset within the selected memory space.

        Corresponds to viIn16* function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Specifies the address space.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        extended : bool, optional
            Use 64 bits offset independent of the platform, False by default.

        Returns
        -------
        int
            Data read from memory
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def in_32(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
extended: bool = False,
) -> Tuple[int, StatusCode]:
"""Reads a 32-bit value at the given offset within the selected memory space.

        Corresponds to viIn32* function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Specifies the address space.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        extended : bool, optional
            Use 64 bits offset independent of the platform, False by default.

        Returns
        -------
        int
            Data read from memory
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def in_64(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
extended: bool = False,
) -> Tuple[int, StatusCode]:
"""Reads a 64-bit value at the given offset within the selected memory space.

        Corresponds to viIn64* function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Specifies the address space.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        extended : bool, optional
            Use 64 bits offset independent of the platform, False by default.

        Returns
        -------
        int
            Data read from memory
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def install_handler(
self,
session: VISASession,
event_type: constants.EventType,
handler: VISAHandler,
user_handle: Any,
) -> Tuple[VISAHandler, Any, Any, StatusCode]:
"""Install handlers for event callbacks.

        Corresponds to viInstallHandler function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        event_type : constants.EventType
            Logical event identifier.
        handler : VISAHandler
            Reference to a handler to be installed by a client application.
        user_handle : Any
            Value specified by an application that can be used for identifying
            handlers uniquely for an event type.

        Returns
        -------
        handler : VISAHandler
            Handler to be installed by a client application.
        converted_user_handle :
            Converted user handle to match the underlying library. This version
            of the handle should be used in further call to the library.
        converted_handler :
            Converted version of the handler satisfying to backend library.
        status_code : StatusCode
            Return value of the library call

        """
        raise NotImplementedError

[docs]
def list_resources(
self, session: VISARMSession, query: str = "?\*::INSTR"
) -> Tuple[str, ...]:
"""Return a tuple of all connected devices matching query.

        Parameters
        ----------
        session : VISARMSession
            Unique logical identifier to the resource manager session.
        query : str
            Regular expression used to match devices.

        Returns
        -------
        Tuple[str, ...]
            Resource names of all the connected devices matching the query.

        """
        raise NotImplementedError

[docs]
def lock(
self,
session: VISASession,
lock_type: constants.Lock,
timeout: int,
requested_key: Optional[str] = None,
) -> Tuple[str, StatusCode]:
"""Establishes an access mode to the specified resources.

        Corresponds to viLock function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        lock_type : constants.Lock
            Specifies the type of lock requested.
        timeout : int
            Absolute time period (in milliseconds) that a resource waits to get
            unlocked by the locking session before returning an error.
        requested_key : Optional[str], optional
            Lock key requested when using a shared lock. For an exclusive lock,
            pass None.

        Returns
        -------
        Optional[str]
            Key for sharing the lock with other sessions, or None when the lock
            is exclusive.
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def map_address(
self,
session: VISASession,
map_space: constants.AddressSpace,
map_base: int,
map_size: int,
access: Literal[False] = False,
suggested: Optional[int] = None,
) -> Tuple[int, StatusCode]:
"""Maps the specified memory space into the process's address space.

        Corresponds to viMapAddress function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        map_space : constants.AddressSpace
            Specifies the address space to map.
        map_base : int
            Offset (in bytes) of the memory to be mapped.
        map_size : int
            Amount of memory to map (in bytes).
        access : False
            Unused parameter.
        suggested : Optional[int], optional
            If not None, asks the operating system to map the memory at the
            requested address. That exact address is not guaranteed; this
            operation may place the memory in a different address region.

        Returns
        -------
        int
            Address in your process space where the memory was mapped
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def map_trigger(
self,
session: VISASession,
trigger_source: constants.InputTriggerLine,
trigger_destination: constants.OutputTriggerLine,
mode: None = None,
) -> StatusCode:
"""Map the specified trigger source line to the specified destination line.

        Corresponds to viMapTrigger function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        trigger_source : constants.InputTriggerLine
            Source line from which to map.
        trigger_destination : constants.OutputTriggerLine
            Destination line to which to map.
        mode : None, optional
            Always None for this version of the VISA specification.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def memory_allocation(
self, session: VISASession, size: int, extended: bool = False
) -> Tuple[int, StatusCode]:
"""Allocate memory from a resource's memory region.

        Corresponds to viMemAlloc* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        size : int
            Specifies the size of the allocation.
        extended : bool, optional
            Use 64 bits offset independent of the platform.

        Returns
        -------
        int
            offset of the allocated memory
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def memory_free(
self, session: VISASession, offset: int, extended: bool = False
) -> StatusCode:
"""Frees memory previously allocated using the memory_allocation() operation.

        Corresponds to viMemFree* function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        offset : int
            Offset of the memory to free.
        extended : bool, optional
            Use 64 bits offset independent of the platform.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def move(
self,
session: VISASession,
source_space: constants.AddressSpace,
source_offset: int,
source_width: constants.DataWidth,
destination_space: constants.AddressSpace,
destination_offset: int,
destination_width: constants.DataWidth,
length: int,
) -> StatusCode:
"""Moves a block of data.

        Corresponds to viMove function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        source_space : constants.AddressSpace
            Specifies the address space of the source.
        source_offset : int
            Offset of the starting address or register from which to read.
        source_width : constants.DataWidth
            Specifies the data width of the source.
        destination_space : constants.AddressSpace
            Specifies the address space of the destination.
        destination_offset : int
            Offset of the starting address or register to which to write.
        destination_width : constants.DataWidth
            Specifies the data width of the destination.
        length: int
            Number of elements to transfer, where the data width of the
            elements to transfer is identical to the source data width.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def move_asynchronously(
self,
session: VISASession,
source_space: constants.AddressSpace,
source_offset: int,
source_width: constants.DataWidth,
destination_space: constants.AddressSpace,
destination_offset: int,
destination_width: constants.DataWidth,
length: int,
) -> Tuple[VISAJobID, StatusCode]:
"""Moves a block of data asynchronously.

        Corresponds to viMoveAsync function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        source_space : constants.AddressSpace
            Specifies the address space of the source.
        source_offset : int
            Offset of the starting address or register from which to read.
        source_width : constants.DataWidth
            Specifies the data width of the source.
        destination_space : constants.AddressSpace
            Specifies the address space of the destination.
        destination_offset : int
            Offset of the starting address or register to which to write.
        destination_width : constants.DataWidth
            Specifies the data width of the destination.
        length : int
            Number of elements to transfer, where the data width of the
            elements to transfer is identical to the source data width.

        Returns
        -------
        VISAJobID
            Job identifier of this asynchronous move operation
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def move_in_8(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
length: int,
extended: bool = False,
) -> Tuple[List[int], StatusCode]:
"""Moves an 8-bit block of data to local memory.

        Corresponds to viMoveIn8* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space from which to move the data.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        length : int
             Number of elements to transfer, where the data width of
