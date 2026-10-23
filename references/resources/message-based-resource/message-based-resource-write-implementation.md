# pyvisa.resources.messagebased.MessageBasedResource.write

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def write(
        self,
        message: str,
        termination: Optional[str] = None,
        encoding: Optional[str] = None,
    ) -> int:
        """Write a string message to the device.

        The write_termination is always appended to it.

        Parameters
        ----------
        message : str
            The message to be sent.
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

        if term:
            if message.endswith(term):
                warnings.warn(
                    "write message already ends with termination characters",
                    stacklevel=2,
                )
            message += term

        count = self.write_raw(message.encode(enco))

        return count
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
