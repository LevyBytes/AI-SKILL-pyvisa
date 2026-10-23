# pyvisa.resources.messagebased.MessageBasedResource.read_raw

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def read_raw(self, size: Optional[int] = None) -> bytes:
        """Read the unmodified string sent from the instrument to the computer.

        In contrast to read(), no termination characters are stripped.

        Parameters
        ----------
        size : Optional[int], optional
            The chunk size to use to perform the reading. Defaults to None,
            meaning the resource wide set value is set.

        Returns
        -------
        bytes
            Bytes read from the instrument.

        """
        return bytes(self._read_raw(size))
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
