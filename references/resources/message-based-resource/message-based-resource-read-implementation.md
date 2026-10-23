# pyvisa.resources.messagebased.MessageBasedResource.read

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def read(
        self, termination: Optional[str] = None, encoding: Optional[str] = None
    ) -> str:
        """Read a string from the device.

        Reading stops when the device stops sending (e.g. by setting
        appropriate bus lines), or the termination characters sequence was
        detected.  Attention: Only the last character of the termination
        characters is really used to stop reading, however, the whole sequence
        is compared to the ending of the read string message.  If they don't
        match, a warning is issued.

        Parameters
        ----------
        termination : Optional[str], optional
            Alternative character termination to use. If None, the value of
            read_termination is used. Defaults to None.
        encoding : Optional[str], optional
            Alternative encoding to use to turn bytes into str. If None, the
            value of encoding is used. Defaults to None.

        Returns
        -------
        str
            Message read from the instrument and decoded.

        """
        enco = self._encoding if encoding is None else encoding

        if termination is None:
            termination = self._read_termination
            message = self._read_raw().decode(enco)
        else:
            with self.read_termination_context(termination):
                message = self._read_raw().decode(enco)

        if not termination:
            return message

        if not message.endswith(termination):
            warnings.warn(
                "read string doesn't end with termination characters", stacklevel=2
            )
            return message

        return message[: -len(termination)]
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
