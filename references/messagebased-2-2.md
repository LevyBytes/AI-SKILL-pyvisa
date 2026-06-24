# Messagebased (part 2) (2)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

        delay = self.query_delay if delay is None else delay
        if delay > 0.0:
            time.sleep(delay)

        return self.read()

[docs]
def query_ascii_values(
self,
message: str,
converter: util.ASCII_CONVERTER = "f",
separator: Union[str, Callable[[str], Iterable[str]]] = ",",
container: Union[Type, Callable[[Iterable], Sequence]] = list,
delay: Optional[float] = None,
) -> Sequence[Any]:
"""Query the device for values in ascii format returning an iterable of
values.

        Parameters
        ----------
        message : str
            The message to send.
        converter : ASCII_CONVERTER, optional
            Str format of function to convert each value. Default to "f".
        separator : Union[str, Callable[[str], Iterable[str]]]
            str or callable used to split the data into individual elements.
            If a str is given, data.split(separator) is used. Default to ",".
        container : Union[Type, Callable[[Iterable], Sequence]], optional
            Container type to use for the output data. Possible values are: list,
            tuple, np.ndarray, etc, Default to list.
        delay : Optional[float], optional
            Delay in seconds between write and read operations. If None,
            defaults to self.query_delay.

        Returns
        -------
        Sequence
            Parsed data.
        """

        self.write(message)
        if delay is None:
            delay = self.query_delay
        if delay > 0.0:
            time.sleep(delay)

        return self.read_ascii_values(converter, separator, container)

[docs]
def query_binary_values(
self,
message: str,
datatype: util.BINARY_DATATYPES = "f",
is_big_endian: bool = False,
container: Union[Type, Callable[[Iterable], Sequence]] = list,
delay: Optional[float] = None,
header_fmt: util.BINARY_HEADERS = "ieee",
expect_termination: bool = True,
data_points: int = 0,
chunk_size: Optional[int] = None,
monitoring_interface: Optional[SupportsUpdate] = None,
length_before_block: Optional[int] = None,
raise_on_late_block: bool = False,
) -> Sequence[Union[int, float]]:
"""Query the device for values in binary format returning an iterable
of values.

        Parameters
        ----------
        message : str
            The message to send.
        datatype : BINARY_DATATYPES, optional
            Format string for a single element. See struct module. 'f' by default.
        is_big_endian : bool, optional
            Are the data in big or little endian order. Defaults to False.
        container : Union[Type, Callable[[Iterable], Sequence]], optional
            Container type to use for the output data. Possible values are: list,
            tuple, np.ndarray, etc, Default to list.
        delay : Optional[float], optional
            Delay in seconds between write and read operations. If None,
            defaults to self.query_delay.
        header_fmt : util.BINARY_HEADERS, optional
            Format of the header prefixing the data. Defaults to 'ieee'.
        expect_termination : bool, optional
            When set to False, the expected length of the binary values block
            does not account for the final termination character
            (the read termination). Defaults to True.
        data_points : int, optional
             Expected point count for the block. This is used only when the
             instrument does not report it itself. It is converted to a byte
             count based on the datatype. Defaults to 0.
        chunk_size : int, optional
            Chunk size used when reading from the device. Larger chunks may be
            faster for large amount of data.
        monitoring_interface : SupportsUpdate Protocol, optional
            Progress monitoring object with update() method that accepts the number
            of bytes read. See the tqdm documentation (a progress bar package) for
            more information.

        Returns
        -------
        Sequence[Union[int, float]]
            Data read from the device.

        """
        if header_fmt not in ("ieee", "hp", "rs", "empty"):
            raise ValueError(
                "Invalid header format. Valid options are 'ieee', 'hp', 'rs', and 'empty'"
            )

        self.write(message)
        if delay is None:
            delay = self.query_delay
        if delay > 0.0:
            time.sleep(delay)

        return self.read_binary_values(
            datatype,
            is_big_endian,
            container,
            header_fmt,
            expect_termination,
            data_points,
            chunk_size,
            monitoring_interface,
            length_before_block,
            raise_on_late_block,
        )

[docs]
def assert_trigger(self) -> None:
"""Sends a software trigger to the device."""
self.visalib.assert_trigger(self.session, constants.TriggerProtocol.default)

    @property
    def stb(self) -> int:
        """Service request status register."""
        return self.read_stb()

[docs]
def read_stb(self) -> int:
"""Service request status register."""
value, \retcode = self.visalib.read_stb(self.session)
return value

[docs]
@contextlib.contextmanager
def read_termination_context(self, new_termination: Optional[str]) -> Iterator:
term = self.read_termination
self.read_termination = new_termination
yield
self.read_termination = term

[docs]
def flush(self, mask: constants.BufferOperation) -> None:
"""Manually clears the specified buffers.

        The mask value can make this write buffered data to the device.

        Parameters
        ----------
        mask : constants.BufferOperation
            Specifies the action to be taken with flushing the buffer.
            See highlevel.VisaLibraryBase.flush for a detailed description.

        """
        self.visalib.flush(self.session, mask)

# Rohde and Schwarz Device via Passport. Not sure which Resource should be.

MessageBasedResource.register(constants.InterfaceType.rsnrp, "INSTR")(
MessageBasedResource
)

```

```
