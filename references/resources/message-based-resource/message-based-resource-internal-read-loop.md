# pyvisa.resources.messagebased.MessageBasedResource._read_raw

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    def _read_raw(
        self,
        size: Optional[int] = None,
        monitoring_interface: Optional[SupportsUpdate] = None,
    ):
        """Read the unmodified string sent from the instrument to the computer.

        In contrast to read(), no termination characters are stripped.

        Parameters
        ----------
        size : Optional[int], optional
            The chunk size to use to perform the reading. Defaults to None,
            meaning the resource wide set value is set.
        monitoring_interface : SupportsUpdate Protocol, optional
            Progress monitoring object with update() method that accepts the number
            of bytes read. See the tqdm documentation (a progress bar package) for
            more information.

        Returns
        -------
        bytearray
            Bytes read from the instrument.

        """
        size = self.chunk_size if size is None else size

        loop_status = constants.StatusCode.success_max_count_read

        ret = bytearray()
        with self.ignore_warning(
            constants.StatusCode.success_device_not_present,
            constants.StatusCode.success_max_count_read,
        ):
            try:
                status = loop_status
                while status == loop_status:
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
            except errors.VisaIOError as e:
                logger.debug(
                    "%s - exception while reading: %s\nBuffer content: %r",
                    self._resource_name,
                    e,
                    ret,
                )
                raise

        return ret
```

[Source license and checked revision](../../pyvisa-source-license.md).
