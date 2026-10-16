# pyvisa.resources.messagebased.MessageBasedResource.query

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def query(self, message: str, delay: Optional[float] = None) -> str:
        """A combination of write(message) and read()

        Parameters
        ----------
        message : str
            The message to send.
        delay : Optional[float], optional
            Delay in seconds between write and read operations. If None,
            defaults to self.query_delay.

        Returns
        -------
        str
            Answer from the device.

        """
        self.write(message)

        delay = self.query_delay if delay is None else delay
        if delay > 0.0:
            time.sleep(delay)

        return self.read()
```

[Source license and checked revision](../../pyvisa-source-license.md).
