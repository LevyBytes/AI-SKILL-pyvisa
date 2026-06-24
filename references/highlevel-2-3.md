# Highlevel (part 2) (3)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

             the elements to transfer is identical to the source data width.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        data : List[int]
            Data read from the bus
        status_code : StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def move_in_16(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
length: int,
extended: bool = False,
) -> Tuple[List[int], StatusCode]:
"""Moves an 16-bit block of data to local memory.

        Corresponds to viMoveIn816 functions of the VISA library.

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
             the elements to transfer is identical to the source data width.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        data : List[int]
            Data read from the bus
        status_code : StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def move_in_32(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
length: int,
extended: bool = False,
) -> Tuple[List]:
"""Moves an 32-bit block of data to local memory.

        Corresponds to viMoveIn32* functions of the VISA library.

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
             the elements to transfer is identical to the source data width.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        data : List[int]
            Data read from the bus
        status_code : StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def move_in_64(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
length: int,
extended: bool = False,
) -> Tuple[List[int], StatusCode]:
"""Moves an 64-bit block of data to local memory.

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
             the elements to transfer is identical to the source data width.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        data : List[int]
            Data read from the bus
        status_code : StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def move_out_8(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
length: int,
data: Iterable[int],
extended: bool = False,
) -> StatusCode:
"""Moves an 8-bit block of data from local memory.

        Corresponds to viMoveOut8* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space into which move the data.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        length : int
            Number of elements to transfer, where the data width of
            the elements to transfer is identical to the source data width.
        data : Iterable[int]
            Data to write to bus.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def move_out_16(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
length: int,
data: Iterable[int],
extended: bool = False,
) -> StatusCode:
"""Moves an 16-bit block of data from local memory.

        Corresponds to viMoveOut16* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space into which move the data.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        length : int
            Number of elements to transfer, where the data width of
            the elements to transfer is identical to the source data width.
        data : Iterable[int]
            Data to write to bus.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def move_out_32(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
length: int,
data: Iterable[int],
extended: bool = False,
) -> StatusCode:
"""Moves an 32-bit block of data from local memory.

        Corresponds to viMoveOut32* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space into which move the data.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        length : int
            Number of elements to transfer, where the data width of
            the elements to transfer is identical to the source data width.
        data : Iterable[int]
            Data to write to bus.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def move_out_64(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
length: int,
data: Iterable[int],
extended: bool = False,
) -> StatusCode:
"""Moves an 64-bit block of data from local memory.

        Corresponds to viMoveOut64* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space into which move the data.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        length : int
            Number of elements to transfer, where the data width of
            the elements to transfer is identical to the source data width.
        data : Iterable[int]
            Data to write to bus.
        extended : bool, optional
            Use 64 bits offset independent of the platform, by default False.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def open(
self,
session: VISARMSession,
resource_name: str,
access_mode: constants.AccessModes = constants.AccessModes.no_lock,
open_timeout: int = constants.VI_TMO_IMMEDIATE,
) -> Tuple[VISASession, StatusCode]:
"""Opens a session to the specified resource.

        Corresponds to viOpen function of the VISA library.

        Parameters
        ----------
        session : VISARMSession
            Resource Manager session (should always be a session returned from
            open_default_resource_manager()).
        resource_name : str
            Unique symbolic name of a resource.
        access_mode : constants.AccessModes, optional
            Specifies the mode by which the resource is to be accessed.
        open_timeout : int
            If the ``access_mode`` parameter requests a lock, then this
            parameter specifies the absolute time period (in milliseconds) that
            the resource waits to get unlocked before this operation returns an
            error.

        Returns
        -------
        VISASession
            Unique logical identifier reference to a session
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def open_default_resource_manager(self) -> Tuple[VISARMSession, StatusCode]:
"""This function returns a session to the Default Resource Manager resource.

        Corresponds to viOpenDefaultRM function of the VISA library.

        Returns
        -------
        VISARMSession
            Unique logical identifier to a Default Resource Manager session
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def out_8(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
data: int,
extended: bool = False,
) -> StatusCode:
"""Write an 8-bit value to the specified memory space and offset.

        Corresponds to viOut8* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space into which to write.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        data : int
            Data to write to bus.
        extended : bool, optional
            Use 64 bits offset independent of the platform.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def out_16(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
data: int,
extended: bool = False,
) -> StatusCode:
"""Write a 16-bit value to the specified memory space and offset.

        Corresponds to viOut16* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space into which to write.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        data : int
            Data to write to bus.
        extended : bool, optional
            Use 64 bits offset independent of the platform.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def out_32(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
data: Iterable[int],
extended: bool = False,
) -> StatusCode:
"""Write a 32-bit value to the specified memory space and offset.

        Corresponds to viOut32* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space into which to write.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        data : int
            Data to write to bus.
        extended : bool, optional
            Use 64 bits offset independent of the platform.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def out_64(
self,
session: VISASession,
space: constants.AddressSpace,
offset: int,
data: Iterable[int],
extended: bool = False,
) -> StatusCode:
"""Write a 64-bit value to the specified memory space and offset.

        Corresponds to viOut64* functions of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        space : constants.AddressSpace
            Address space into which to write.
        offset : int
            Offset (in bytes) of the address or register from which to read.
        data : int
            Data to write to bus.
        extended : bool, optional
            Use 64 bits offset independent of the platform.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def parse_resource(
self, session: VISARMSession, resource_name: str
) -> Tuple[ResourceInfo, StatusCode]:
"""Parse a resource string to get the interface information.

        Corresponds to viParseRsrc function of the VISA library.

        Parameters
        ----------
        session : VISARMSession
            Resource Manager session (should always be the Default Resource
            Manager for VISA returned from open_default_resource_manager()).
        resource_name : str
             Unique symbolic name of a resource.

        Returns
        -------
        ResourceInfo
            Resource information with interface type and board number
        StatusCode
            Return value of the library call.

        """
        ri, status = self.parse_resource_extended(session, resource_name)
        if status == StatusCode.success:
            return (
                ResourceInfo(
                    ri.interface_type, ri.interface_board_number, None, None, None
                ),
                StatusCode.success,
            )
        else:
            return ri, status

[docs]
def parse_resource_extended(
self, session: VISARMSession, resource_name: str
) -> Tuple[ResourceInfo, StatusCode]:
"""Parse a resource string to get extended interface information.

        Corresponds to viParseRsrcEx function of the VISA library.

        Parameters
        ----------
        session : VISARMSession
            Resource Manager session (should always be the Default Resource
            Manager for VISA returned from open_default_resource_manager()).
        resource_name : str
             Unique symbolic name of a resource.

        Returns
        -------
        ResourceInfo
            Resource information with interface type and board number
        StatusCode
            Return value of the library call.

        """
        try:
            parsed = rname.parse_resource_name(resource_name)
        except ValueError:
            return (
                ResourceInfo(constants.InterfaceType.unknown, 0, None, None, None),
                StatusCode.error_invalid_resource_name,
            )

        board_number: Optional[int]
        try:
            # We can only get concrete classes which have one of those attributes
            board_number = int(
                parsed.board  # type: ignore
                if hasattr(parsed, "board")
                else parsed.interface  # type: ignore
            )
        # In some cases the board number may not be convertible to an int
        # PyVISA-py serial resources on Linux for example. For VICP, there is
        # no such attribute.
        except (ValueError, AttributeError):
            board_number = None

        return (
            ResourceInfo(
                parsed.interface_type_const,
                board_number,
                parsed.resource_class,
                str(parsed),
                None,
            ),
            StatusCode.success,
        )

[docs]
def peek_8(
self, session: VISASession, address: VISAMemoryAddress
) -> Tuple[int, StatusCode]:
"""Read an 8-bit value from the specified address.

        Corresponds to viPeek8 function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.

        Returns
        -------
        int
            Data read from bus
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def peek_16(
self, session: VISASession, address: VISAMemoryAddress
) -> Tuple[int, StatusCode]:
"""Read an 16-bit value from the specified address.

        Corresponds to viPeek16 function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.

        Returns
        -------
        int
            Data read from bus
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def peek_32(
self, session: VISASession, address: VISAMemoryAddress
) -> Tuple[int, StatusCode]:
"""Read an 32-bit value from the specified address.

        Corresponds to viPeek32 function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.

        Returns
        -------
        int
            Data read from bus
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def peek_64(
self, session: VISASession, address: VISAMemoryAddress
) -> Tuple[int, StatusCode]:
"""Read an 64-bit value from the specified address.

        Corresponds to viPeek64 function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.

        Returns
        -------
        int
            Data read from bus
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def poke_8(
self, session: VISASession, address: VISAMemoryAddress, data: int
) -> StatusCode:
"""Write an 8-bit value to the specified address.

        Corresponds to viPoke8 function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.
        data : int
            Data to write.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def poke_16(
self, session: VISASession, address: VISAMemoryAddress, data: int
) -> StatusCode:
"""Write an 16-bit value to the specified address.

        Corresponds to viPoke16 function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.
        data : int
            Data to write.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def poke_32(
self, session: VISASession, address: VISAMemoryAddress, data: int
) -> StatusCode:
"""Write an 32-bit value to the specified address.

        Corresponds to viPoke32 function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.
        data : int
            Data to write.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def poke_64(
self, session: VISASession, address: VISAMemoryAddress, data: int
) -> StatusCode:
"""Write an 64-bit value to the specified address.

        Corresponds to viPoke64 function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        address : VISAMemoryAddress
            Source address to read the value.
        data : int
            Data to write.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def read(self, session: VISASession, count: int) -> Tuple[bytes, StatusCode]:
"""Reads data from device or interface synchronously.

        Corresponds to viRead function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        count : int
            Number of bytes to be read.

        Returns
        -------
        bytes
            Date read
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def read_asynchronously(
self, session: VISASession, count: int
) -> Tuple[SupportsBytes, VISAJobID, StatusCode]:
"""Reads data from device or interface asynchronously.

        Corresponds to viReadAsync function of the VISA library. Since the
        asynchronous operation may complete before the function call return
        implementation should make sure that get_buffer_from_id will be able
        to return the proper buffer before this method returns.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        count : int
            Number of bytes to be read.

        Returns
        -------
        SupportsBytes
            Buffer that will be filled during the asynchronous operation.
        VISAJobID
            Id of the asynchronous job
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError

[docs]
def get_buffer_from_id(self, job_id: VISAJobID) -> Optional[SupportsBytes]:
"""Retrieve the buffer associated with a job id created in read_asynchronously

        Parameters
        ----------
        job_id : VISAJobID
            Id of the job for which to retrieve the buffer.

        Returns
        -------
        Optional[SupportsBytes]
            Data storage buffer, or None when the job id is not associated with
            any job.

        """
        raise NotImplementedError

[docs]
def read_stb(self, session: VISASession) -> Tuple[int, StatusCode]:
"""Reads a status byte of the service request.

        Corresponds to viReadSTB function of the VISA library.

        Parameters
        ----------
