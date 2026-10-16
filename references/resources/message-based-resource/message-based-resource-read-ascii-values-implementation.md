# pyvisa.resources.messagebased.MessageBasedResource.read_ascii_values

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def read_ascii_values(
        self,
        converter: util.ASCII_CONVERTER = "f",
        separator: Union[str, Callable[[str], Iterable[str]]] = ",",
        container: Union[Type, Callable[[Iterable], Sequence]] = list,
    ) -> Sequence:
        """Read values from the device in ascii format returning an iterable of
        values.

        Parameters
        ----------
         converter : ASCII_CONVERTER, optional
            Str format of function to convert each value. Default to "f".
        separator : Union[str, Callable[[str], Iterable[str]]]
            str or callable used to split the data into individual elements.
            If a str is given, data.split(separator) is used. Default to ",".
        container : Union[Type, Callable[[Iterable], Sequence]], optional
            Container type to use for the output data. Possible values are: list,
            tuple, np.ndarray, etc, Default to list.

        Returns
        -------
        Sequence
            Parsed data.

        """
        # Use read rather than _read_raw because we cannot handle a bytearray
        block = self.read()

        return util.from_ascii_block(block, converter, separator, container)
```

[Source license and checked revision](../../pyvisa-source-license.md).
