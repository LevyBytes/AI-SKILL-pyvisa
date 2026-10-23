# pyvisa.resources.messagebased.MessageBasedResource.query_ascii_values

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
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
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
