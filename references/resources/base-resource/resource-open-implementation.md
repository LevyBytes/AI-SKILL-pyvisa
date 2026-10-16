# pyvisa.resources.resource.Resource.open

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md) / [Enclosing source class declaration](resource-implementation.md) / [Source module imports and declarations](resource-module-imports-implementation.md)

```python
    def open(
        self,
        access_mode: constants.AccessModes = constants.AccessModes.no_lock,
        open_timeout: int = 5000,
    ) -> None:
        """Opens a session to the specified resource.

        Parameters
        ----------
        access_mode : constants.AccessModes, optional
            Specifies the mode by which the resource is to be accessed.
            Defaults to constants.AccessModes.no_lock.
        open_timeout : int, optional
            If the ``access_mode`` parameter requests a lock, then this parameter
            specifies the absolute time period (in milliseconds) that the
            resource waits to get unlocked before this operation returns an error.
            Defaults to 5000.

        """
        logger.debug("%s - opening ...", self._resource_name, extra=self._logging_extra)
        with self._resource_manager.ignore_warning(
            constants.StatusCode.success_device_not_present
        ):
            self.session, status = self._resource_manager.open_bare_resource(
                self._resource_name, access_mode, open_timeout
            )

            if status == constants.StatusCode.success_device_not_present:
                # The device was not ready when we opened the session.
                # Now it gets five seconds more to become ready.
                # Every 0.1 seconds we probe it with viClear.
                start_time = time.time()
                sleep_time = 0.1
                try_time = 5
                while time.time() - start_time < try_time:
                    time.sleep(sleep_time)
                    try:
                        self.clear()
                        break
                    except errors.VisaIOError as error:
                        if error.error_code != constants.StatusCode.error_no_listeners:
                            raise

        self._logging_extra["session"] = self.session
        logger.debug(
            "%s - is open with session %s",
            self._resource_name,
            self.session,
            extra=self._logging_extra,
        )
```

[Source license and checked revision](../../pyvisa-source-license.md).
