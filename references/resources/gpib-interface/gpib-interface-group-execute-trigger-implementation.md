# pyvisa.resources.gpib.GPIBInterface.group_execute_trigger

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](gpib-interface-implementation.md) / [Source module imports and declarations](../gpib/gpib-module-imports-implementation.md)

```python
    def group_execute_trigger(
        self, *resources: GPIBInstrument
    ) -> Tuple[int, constants.StatusCode]:
        """

        Parameters
        ----------
        resources : GPIBInstrument
            GPIB resources to which to send the group trigger.

        Returns
        -------
        int
            Number of bytes written as part of sending the GPIB commands.
        constants.StatusCode
            Return value of the library call.

        """
        board_number = None
        for resource in resources:
            if not isinstance(resource, GPIBInstrument):
                raise ValueError(f"{resource!r} is not a GPIBInstrument")

            device_board = resource.interface_number
            if board_number is not None and board_number != device_board:
                raise ValueError(
                    f"{resource!r} is attached to board {device_board} but "
                    f"another device is attached to board {board_number}"
                )
            elif board_number is None:
                board_number = device_board

        if not self.is_controller_in_charge:
            self.send_ifc()

        # Broadcast board as talker and unlisten to all devices
        # Based on VISA address format for INTFC we cannot have a secondary address
        command = GPIBCommand.talker(self.primary_address) + GPIBCommand.unlisten

        for resource in resources:
            command += GPIBCommand.listener(
                resource.primary_address
            ) + GPIBCommand.secondary_address(resource.secondary_address)

        # send GET ('group execute trigger')
        command += GPIBCommand.group_execute_trigger

        return self.send_command(command)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
