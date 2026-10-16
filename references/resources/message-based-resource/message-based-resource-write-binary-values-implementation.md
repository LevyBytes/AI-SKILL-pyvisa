# pyvisa.resources.messagebased.MessageBasedResource.write_binary_values

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def write_binary_values(
        self,
        message: str,
        values: Sequence[Any],
        datatype: util.BINARY_DATATYPES = "f",
        is_big_endian: bool = False,
        termination: Optional[str] = None,
        encoding: Optional[str] = None,
        header_fmt: util.BINARY_HEADERS = "ieee",
    ):
        """Write a string message to the device followed by values in binary format.

        The write_termination is always appended to it.

        Parameters
        ----------
        message : str
            The header of the message to be sent.
        values : Sequence[Any]
            Data to be written to the device.
        datatype : util.BINARY_DATATYPES, optional
            The format string for a single element. See struct module.
        is_big_endian : bool, optional
            Are the data in big or little endian order.
        termination : Optional[str], optional
            Alternative character termination to use. If None, the value of
            write_termination is used. Defaults to None.
        encoding : Optional[str], optional
            Alternative encoding to use to turn str into bytes. If None, the
            value of encoding is used. Defaults to None.
        header_fmt : util.BINARY_HEADERS
            Format of the header prefixing the data.

        Returns
        -------
        int
            Number of bytes written.

        """
        term = self._write_termination if termination is None else termination
        enco = self._encoding if encoding is None else encoding

        if term and message.endswith(term):
            warnings.warn(
                "write message already ends with termination characters",
                stacklevel=2,
            )

        if header_fmt == "ieee":
            block = util.to_ieee_block(values, datatype, is_big_endian)
        elif header_fmt == "rs":
            block = util.to_rs_block(values, datatype, is_big_endian)
        elif header_fmt == "hp":
            block = util.to_hp_block(values, datatype, is_big_endian)
        elif header_fmt == "empty":
            block = util.to_binary_block(values, b"", datatype, is_big_endian)
        else:
            raise ValueError("Unsupported header_fmt: %s" % header_fmt)

        msg = message.encode(enco) + block

        if term:
            msg += term.encode(enco)

        count = self.write_raw(msg)

        return count
```

[Source license and checked revision](../../pyvisa-source-license.md).
