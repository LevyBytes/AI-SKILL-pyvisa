# pyvisa.resources.gpib.GPIBCommand

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Source module imports and declarations](gpib-module-imports-implementation.md)

```python
class GPIBCommand(bytes, Enum):
    """GPIB commands to use in send_command.

    Please note that group_execute_trigger provide a high level interface to
    perform a trigger addressed to multiple instrument on the bus.

    See: https://www.ni.com/docs/en-US/bundle/gpib-for-labview-nxg/page/ieee-488-command-messages.html
    for the complete list of GPIB commands.

    """

    #: GTL: GO TO LOCAL affects only addressed devices
    go_to_local = GTL = b"\x01"

    #: SDC: SELECTED DEVICE CLEAR
    selected_device_clear = SDC = b"\x04"

    #: PPC: PARALLEL POLL CONFIGURE
    parallel_poll_configure = PPC = b"\x05"

    #: PPU: PARALLEL POLL UNCONFIGURE
    parallel_poll_unconfigure = PPU = b"\x15"

    #: GET: GROUP EXECUTE TRIGGER
    group_execute_trigger = GET = b"\x08"

    #: TCT: TAKE CONTROL
    take_control = TCT = b"\x09"

    #: LLO: LOCAL LOCKOUT
    local_lockout = LLO = b"\x11"

    #: DCL: DEVICE CLEAR
    device_clear = DCL = b"\x14"

    #: SPE: SERIAL POLL ENABLE
    serial_poll_enable = SPE = b"\x18"

    #: SPD: SERIAL POLL DISABLE
    serial_poll_disable = SPD = b"\x19"

    #: CFE: CONFIGURE ENABLE
    configure_enable = CFE = b"\x1f"

    #: UNT: UNTALK
    untalk = UNT = b"\x5f"

    #: UNL: UNLISTEN
    unlisten = UNL = b"\x3f"
```

[Source license and checked revision](../../pyvisa-source-license.md).
