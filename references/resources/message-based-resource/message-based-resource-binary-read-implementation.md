# MessageBasedResource.read_binary_values implementation: headers, lengths, termination and conversion errors

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Full binary-reader signature and contract](message-based-resource-binary-read-contract.md) / [MessageBasedResource declaration](message-based-resource-implementation.md) / [Read termination state](message-based-resource-implementation.md) / [read_bytes completion helper](message-based-resource-read-bytes-implementation.md) / [_read_raw backend helper](message-based-resource-internal-read-loop.md) / [Module imports and protocol context](messagebased-module-imports-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def read_binary_values(
        self,
        datatype: util.BINARY_DATATYPES = "f",
        is_big_endian: bool = False,
        container: Union[Type, Callable[[Iterable], Sequence]] = list,
        header_fmt: util.BINARY_HEADERS = "ieee",
        expect_termination: bool = True,
        data_points: int = -1,
        chunk_size: Optional[int] = None,
        monitoring_interface: Optional[SupportsUpdate] = None,
        length_before_block: Optional[int] = None,
        raise_on_late_block: bool = False,
    ) -> Sequence[Union[int, float]]:
        block = self._read_raw(chunk_size, monitoring_interface=monitoring_interface)

        if header_fmt == "ieee":
            offset, data_length = util.parse_ieee_block_header(
                block, length_before_block, raise_on_late_block
            )

        elif header_fmt == "rs":
            offset, data_length = util.parse_ieee_or_rs_block_header(
                block, length_before_block, raise_on_late_block
            )
        elif header_fmt == "hp":
            offset, data_length = util.parse_hp_block_header(
                block, is_big_endian, length_before_block, raise_on_late_block
            )
        elif header_fmt == "empty":
            offset = 0
            data_length = -1
        else:
            raise ValueError(
                "Invalid header format. Valid options are 'ieee', 'empty', 'hp', 'rs'"
            )

        # Allow to support instrument such as the Keithley 2000 that do not
        # report the length of the block
        data_length = (
            data_length if data_length >= 0 else data_points * struct.calcsize(datatype)
        )

        expected_length = offset + data_length

        if expect_termination and self._read_termination is not None:
            expected_length += len(self._read_termination)

        # Read all the data if we know what to expect.
        if data_length > 0:
            block.extend(
                self.read_bytes(
                    expected_length - len(block),
                    chunk_size=chunk_size,
                    monitoring_interface=monitoring_interface,
                )
            )
        elif data_length == 0:
            pass
        else:
            raise ValueError(
                "The length of the data to receive could not be "
                "determined. You should provide the number of "
                "points you expect using the data_points keyword "
                "argument."
            )

        try:
            # Do not reparse the headers since it was already done and since
            # this allows for custom data length
            return util.from_binary_block(
                block, offset, data_length, datatype, is_big_endian, container
            )
        except ValueError as e:
            raise errors.InvalidBinaryFormat(e.args[0])
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
