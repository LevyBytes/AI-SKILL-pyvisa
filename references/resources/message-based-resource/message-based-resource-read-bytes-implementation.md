# pyvisa.resources.messagebased.MessageBasedResource.read_bytes

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def read_bytes(
        self,
        count: int,
        chunk_size: Optional[int] = None,
        break_on_termchar: bool = False,
        monitoring_interface: Optional[SupportsUpdate] = None,
    ) -> bytes:
        """Read a certain number of bytes from the instrument.

        Parameters
        ----------
        count : int
            The number of bytes to read from the instrument.
        chunk_size : Optional[int], optional
            The chunk size to use to perform the reading. If count > chunk_size
            multiple low level operations will be performed. Defaults to None,
            meaning the resource wide set value is set.
        break_on_termchar : bool, optional
            Should the reading stop when a termination character is encountered
            or when the message ends. Defaults to False.
        monitoring_interface : SupportsUpdate Protocol, optional
            Progress monitoring object with update() method that accepts the number
            of bytes read. See the tqdm documentation (a progress bar package) for
            more information.

        Returns
        -------
        bytes
            Bytes read from the instrument.

        """
        chunk_size = chunk_size or self.chunk_size
        ret = bytearray()
        left_to_read = count
        success = constants.StatusCode.success
        termchar_read = constants.StatusCode.success_termination_character_read

        with self.ignore_warning(
            constants.StatusCode.success_device_not_present,
            constants.StatusCode.success_max_count_read,
        ):
            try:
                status = None
                while len(ret) < count:
                    size = min(chunk_size, left_to_read)
                    logger.debug(
                        "%s - reading %d bytes (last status %r)",
                        self._resource_name,
                        size,
                        status,
                    )
                    chunk, status = self.visalib.read(self.session, size)
                    if monitoring_interface:
                        monitoring_interface.update(len(chunk))
                    ret.extend(chunk)
                    left_to_read -= len(chunk)
                    if break_on_termchar and (
                        status == success or status == termchar_read
                    ):
                        break
            except errors.VisaIOError as e:
                logger.debug(
                    "%s - exception while reading: %s\nBuffer content: %r",
                    self._resource_name,
                    e,
                    ret,
                )
                raise
        return bytes(ret)
```

[Source license and checked revision](../../pyvisa-source-license.md).
