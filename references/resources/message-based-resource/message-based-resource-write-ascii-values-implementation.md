# pyvisa.resources.messagebased.MessageBasedResource.write_ascii_values

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def write_ascii_values(
        self,
        message: str,
        values: Iterable[Any],
        converter: util.ASCII_CONVERTER = "f",
        separator: Union[str, Callable[[Iterable[str]], str]] = ",",
        termination: Optional[str] = None,
        encoding: Optional[str] = None,
    ):
        """Write a string message to the device followed by values in ascii format.

        The write_termination is always appended to it.

        Parameters
        ----------
        message : str
            Header of the message to be sent.
        values : Sequence[Any]
            Data to be written to the device.
        converter : Union[str, Callable[[Any], str]], optional
            Str formatting codes or function used to convert each value.
            Defaults to "f".
        separator : Union[str, Callable[[Iterable[str]], str]], optional
            Str or callable that join the values in a single str.
            If a str is given, separator.join(values) is used. Defaults to ','
        termination : Optional[str], optional
            Alternative character termination to use. If None, the value of
            write_termination is used. Defaults to None.
        encoding : Optional[str], optional
            Alternative encoding to use to turn str into bytes. If None, the
            value of encoding is used. Defaults to None.

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

        block = util.to_ascii_block(values, converter, separator)

        msg = message.encode(enco) + block.encode(enco)

        if term:
            msg += term.encode(enco)

        count = self.write_raw(msg)

        return count
```

[Source license and checked revision](../../pyvisa-source-license.md).
