# Constants (part 2) (2)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

VI_UTIL_ASSERT_SYSFAIL = 2
VI_UTIL_DEASSERT_SYSFAIL = 3

VI_VXI_CLASS_MEMORY = 0
VI_VXI_CLASS_EXTENDED = 1
VI_VXI_CLASS_MESSAGE = 2
VI_VXI_CLASS_REGISTER = 3
VI_VXI_CLASS_OTHER = 4

VI_PXI_LBUS_UNKNOWN = -1
VI_PXI_LBUS_NONE = 0
VI_PXI_LBUS_STAR_TRIG_BUS_0 = 1000
VI_PXI_LBUS_STAR_TRIG_BUS_1 = 1001
VI_PXI_LBUS_STAR_TRIG_BUS_2 = 1002
VI_PXI_LBUS_STAR_TRIG_BUS_3 = 1003
VI_PXI_LBUS_STAR_TRIG_BUS_4 = 1004
VI_PXI_LBUS_STAR_TRIG_BUS_5 = 1005
VI_PXI_LBUS_STAR_TRIG_BUS_6 = 1006
VI_PXI_LBUS_STAR_TRIG_BUS_7 = 1007
VI_PXI_LBUS_STAR_TRIG_BUS_8 = 1008
VI_PXI_LBUS_STAR_TRIG_BUS_9 = 1009
VI_PXI_STAR_TRIG_CONTROLLER = 1413
VI_PXI_LBUS_SCXI = 2000
VI_PXI_ALLOC_SPACE = 9
VI_PXI_CFG_SPACE = 10
VI_PXI_BAR0_SPACE = 11
VI_PXI_BAR1_SPACE = 12
VI_PXI_BAR2_SPACE = 13
VI_PXI_BAR3_SPACE = 14
VI_PXI_BAR4_SPACE = 15
VI_PXI_BAR5_SPACE = 16

VI_PXI_ADDR_NONE = 0
VI_PXI_ADDR_MEM = 1
VI_PXI_ADDR_IO = 2
VI_PXI_ADDR_CFG = 3

VI_USB_PIPE_STATE_UNKNOWN = -1
VI_USB_PIPE_READY = 0
VI_USB_PIPE_STALLED = 1

# From VI_ATTR_USB_END_IN

VI_USB_END_NONE = 0
VI_USB_END_SHORT = 4
VI_USB_END_SHORT_OR_COUNT = 5

# "Backwards compatibility" according to NI

VI_NORMAL = VI_PROT_NORMAL
VI_FDC = VI_PROT_FDC
VI_HS488 = VI_PROT_HS488
VI_ASRL488 = VI_PROT_4882_STRS
VI_ASRL_IN_BUF = VI_IO_IN_BUF
VI_ASRL_OUT_BUF = VI_IO_OUT_BUF
VI_ASRL_IN_BUF_DISCARD = VI_IO_IN_BUF_DISCARD
VI_ASRL_OUT_BUF_DISCARD = VI_IO_OUT_BUF_DISCARD

# fmt: on

# ======================================================================================

# --- Enumeration for easier handling of the constants ---------------------------------

# ======================================================================================

@enum.unique
class VisaBoolean(enum.IntEnum):
"""Visa boolean values."""

    true = VI_TRUE
    false = VI_FALSE

# Constants useful for all kind of resources.

@enum.unique
class Timeouts(enum.IntEnum):
"""Special timeout values."""

    #: Minimal timeout value
    immediate = VI_TMO_IMMEDIATE

    #: Infinite timeout
    infinite = VI_TMO_INFINITE

@enum.unique
class Lock(enum.IntEnum):
"""Kind of lock to use when locking a resource."""

    #: Obtains a exclusive lock on the VISA resource.
    exclusive = VI_EXCLUSIVE_LOCK

    #: Obtains a lock on the VISA resouce which may be shared
    #: between multiple VISA sessions.
    shared = VI_SHARED_LOCK

[docs]
@enum.unique
class AccessModes(enum.IntEnum):
"""Whether and how to lock a resource when opening a connection."""

    #: Does not obtain any lock on the VISA resource.
    no_lock = VI_NO_LOCK

    #: Obtains a exclusive lock on the VISA resource.
    exclusive_lock = VI_EXCLUSIVE_LOCK

    #: Obtains a lock on the VISA resouce which may be shared
    #: between multiple VISA sessions.
    shared_lock = VI_SHARED_LOCK

[docs]
@enum.unique
class InterfaceType(enum.IntEnum):
"""The hardware interface."""

    # Used for unknown interface type strings.
    unknown = -1

    #: GPIB Interface.
    gpib = VI_INTF_GPIB

    #: VXI (VME eXtensions for Instrumentation), VME, MXI (Multisystem eXtension Interface).
    vxi = VI_INTF_VXI

    #: GPIB VXI (VME eXtensions for Instrumentation).
    gpib_vxi = VI_INTF_GPIB_VXI

    #: Serial devices connected to either an RS-232 or RS-485 controller.
    asrl = VI_INTF_ASRL

    #: PXI device.
    pxi = VI_INTF_PXI

    #: TCPIP device.
    tcpip = VI_INTF_TCPIP

    #: Universal Serial Bus (USB) hardware bus.
    usb = VI_INTF_USB

    #: Rio device.
    rio = VI_INTF_RIO

    #: Firewire device.
    firewire = VI_INTF_FIREWIRE

    #: Rohde and Schwarz Device via Passport
    rsnrp = 33024

    #: Lecroy VICP via passport
    vicp = 36000  # FIXME

    #: prologix usb
    prlgx_asrl = 34567  # an arbitrarily chosen value

    #: prologix tcpip
    prlgx_tcpip = 76543  # an arbitrarily chosen value

[docs]
@enum.unique
class LineState(enum.IntEnum):
"""State of a hardware line or signal.

    The line for which the state can be queried are:
    - ASRC resource: BREAK, CTS, DCD, DSR, DTR, RI, RTS signals
    - GPIB resources: ATN, NDAC, REN, SRQ lines
    - VXI BACKPLANE:  VXI/VME SYSFAIL backplane line

    Search for LineState in attributes.py for more details.

    """

    #: The line/signal is currently asserted
    asserted = VI_STATE_ASSERTED

    #: The line/signal is currently deasserted
    unasserted = VI_STATE_UNASSERTED

    #: The state of the line/signal is unknown
    unknown = VI_STATE_UNKNOWN

[docs]
@enum.unique
class IOProtocol(enum.IntEnum):
"""IO protocol used for communication.

    See attributes.AttrVI_ATTR_IO_PROT for more details.

    """

    normal = VI_PROT_NORMAL

    #: Fast data channel (FDC) protocol for VXI
    fdc = VI_PROT_FDC

    #: High speed 488 transfer for GPIB
    hs488 = VI_PROT_HS488

    #: 488 style transfer for serial
    protocol4882_strs = VI_PROT_4882_STRS

    #: Test measurement class vendor specific for USB
    usbtmc_vendor = VI_PROT_USBTMC_VENDOR

@enum.unique
class EventMechanism(enum.IntEnum):
"""The available event mechanisms for event handling."""

    #: Queue events that can then be queried using wait_on_event
    queue = VI_QUEUE

    #: Use a specified callback handler to deal with events
    handler = VI_HNDLR

    #: Queue events to be passed to the handler when the system is switch to the
    #: handler mechanism.
    suspend_handler = VI_SUSPEND_HNDLR

    #: Use to disable or discard events no matter the handling mechanism
    all = VI_ALL_MECH

# Message based resources relevant constants

@enum.unique
class EventType(enum.IntEnum):
"""The available event types for event handling."""

    #: Notification that an asynchronous operation has completed.
    io_completion = VI_EVENT_IO_COMPLETION

    #: Notification that a trigger interrupt was received from the device.
    #: For VISA, the only triggers that can be sensed are VXI hardware triggers
    #: on the assertion edge (SYNC and ON trigger protocols only).
    trig = VI_EVENT_TRIG

    #: Notification that a service request was received from the device.
    service_request = VI_EVENT_SERVICE_REQ

    #: Notification that the local controller has been sent a device clear message.
    clear = VI_EVENT_CLEAR

    #: Notification that an error condition has occurred during an operation
    #: invocation.
    exception = VI_EVENT_EXCEPTION

    #: Notification that the GPIB controller has gained or lost CIC (controller
    #: in charge) status.
    gpib_controller_in_charge = VI_EVENT_GPIB_CIC

    #: Notification that the GPIB controller has been addressed to talk.
    gpib_talk = VI_EVENT_GPIB_TALK

    #: Notification that the GPIB controller has been addressed to listen.
    gpib_listen = VI_EVENT_GPIB_LISTEN

    #: Notification that the VXI/VME SYSFAIL* line has been asserted.
    vxi_vme_sysfail = VI_EVENT_VXI_VME_SYSFAIL

    #: Notification that the VXI/VME SYSRESET* line has been asserted.
    vxi_vme_sysreset = VI_EVENT_VXI_VME_SYSRESET

    #: Notification that a VXIbus signal or VXIbus interrupt was received from
    #: the device.
    vxi_signal_interrupt = VI_EVENT_VXI_SIGP

    #: Notification that a VXIbus interrupt was received from the device.
    vxi_vme_interrupt = VI_EVENT_VXI_VME_INTR

    #: Notification that a PCI Interrupt was received from the device.
    pxi_interrupt = VI_EVENT_PXI_INTR

    #: Notification that a TCP/IP connection has been made.
    tcpip_connect = VI_EVENT_TCPIP_CONNECT

    #: Notification that a vendor-specific USB interrupt was received from the device.
    usb_interrupt = VI_EVENT_USB_INTR

    #: Value equivalent to all events. Use to switch handling mechanism for all
    #: events in one call or disabling all events.
    all_enabled = VI_ALL_ENABLED_EVENTS

@enum.unique
class BufferType(enum.IntFlag):
"""Buffer potentially available on a message based resource.

    Used with the set_buffer function to alter the size of a buffer.

    """

    #: Formatted read buffer
    read = VI_READ_BUF

    #: Formatted write buffer
    write = VI_WRITE_BUF

    #: I/O communication receive buffer.
    io_in = VI_IO_IN_BUF

    #: I/O communication transmit buffer.
    io_out = VI_IO_OUT_BUF

@enum.unique
class BufferOperation(enum.IntFlag):
"""Possible action of the buffer when performing a flush."""

    #: Discard the read buffer contents and if data was present in the read buffer
    #: and no END-indicator was present, read from the device until encountering
    #: an END indicator (which causes the loss of data).
    discard_read_buffer = VI_READ_BUF

    #: Discard the read buffer contents (does not perform any I/O to the device).
    discard_read_buffer_no_io = VI_READ_BUF_DISCARD

    #: Flush the write buffer by writing all buffered data to the device.
    flush_write_buffer = VI_WRITE_BUF

    #: Discard the write buffer contents (does not perform any I/O to the device).
    discard_write_buffer = VI_WRITE_BUF_DISCARD

    #: Discard the receive buffer contents (does not perform any I/O to the device).
    discard_receive_buffer = VI_IO_IN_BUF_DISCARD

    #: Discards the receive buffer contents (same as VI_IO_IN_BUF_DISCARD)
    discard_receive_buffer2 = VI_IO_IN_BUF

    #: Flush the transmit buffer by writing all buffered data to the device.
    flush_transmit_buffer = VI_IO_OUT_BUF

    #: Discard the transmit buffer contents (does not perform any I/O to the device).
    discard_transmit_buffer = VI_IO_OUT_BUF_DISCARD

# Constants related to serial resources

[docs]
@enum.unique
class StopBits(enum.IntEnum):
"""Number of stop bits marking the end of a frame on a serial resource.

    Used only for ASRL resources.

    """

    one = VI_ASRL_STOP_ONE
    one_and_a_half = VI_ASRL_STOP_ONE5
    two = VI_ASRL_STOP_TWO

[docs]
@enum.unique
class Parity(enum.IntEnum):
"""Parity setting applied to every frame transmitted and received on a serial session.

    Used only for ASRL resources.

    """

    none = VI_ASRL_PAR_NONE
    odd = VI_ASRL_PAR_ODD
    even = VI_ASRL_PAR_EVEN
    mark = VI_ASRL_PAR_MARK
    space = VI_ASRL_PAR_SPACE

[docs]
@enum.unique
class SerialTermination(enum.IntEnum):
"""The available methods for terminating a serial transfer."""

    #: The transfer terminates when all requested data is transferred
    #: or when an error occurs.
    none = VI_ASRL_END_NONE

    #: The transfer occurs with the last bit not set until the last
    #: character is sent.
    last_bit = VI_ASRL_END_LAST_BIT

    #: The transfer terminate by searching for "/"
    #: appending the termination character.
    termination_char = VI_ASRL_END_TERMCHAR

    #: The write transmits a break after all the characters for the
    #: write are sent.
    termination_break = VI_ASRL_END_BREAK

@enum.unique
class WireMode(enum.IntEnum):
"""Valid modes for National Instruments hardware supporting it."""

    #: 4-wire mode.
    rs485_4 = VI_ASRL_WIRE_485_4

    #: 2-wire DTR mode controlled with echo.
    rs485_2_dtr_echo = VI_ASRL_WIRE_485_2_DTR_ECHO

    #: 2-wire DTR mode controlled without echo
    rs485_2_dtr_ctrl = VI_ASRL_WIRE_485_2_DTR_CTRL

    #: 2-wire auto mode controlled with TXRDY
    rs485_2_auto = VI_ASRL_WIRE_485_2_AUTO

    #: Use DTE mode
    rs232_dte = VI_ASRL_WIRE_232_DTE

    #: Use DCE mode
    rs232_dce = VI_ASRL_WIRE_232_DCE

    #: Auto detect the mode to use
    rs232_auto = VI_ASRL_WIRE_232_AUTO

    #: Unknown mode
    unknown = VI_STATE_UNKNOWN

@enum.unique
class ControlFlow(enum.IntFlag):
"""Control flow for a serial resource."""

    none = VI_ASRL_FLOW_NONE
    xon_xoff = VI_ASRL_FLOW_XON_XOFF
    rts_cts = VI_ASRL_FLOW_RTS_CTS
    dtr_dsr = VI_ASRL_FLOW_DTR_DSR

# USB specific constants

@enum.unique
class USBEndInput(enum.IntEnum):
"""Method used to terminate input on USB RAW."""

    none = VI_USB_END_NONE
    short = VI_USB_END_SHORT
    short_or_count = VI_USB_END_SHORT_OR_COUNT

# GPIB specific value

[docs]
@enum.unique
class AddressState(enum.IntEnum):
"""State of a GPIB resource.

    Corresponds to the Attribute.GPIB_address_state attribute

    """

    #: The resource is unadressed
    unaddressed = VI_GPIB_UNADDRESSED

    #: The resource is addressed to talk
    talker = VI_GPIB_TALKER

    #: The resource is addressed to listen
    listenr = VI_GPIB_LISTENER

@enum.unique
class ATNLineOperation(enum.IntEnum):
"""Operation that can be performed on the GPIB ATN line.

    These operations are available only to GPIB INTFC resources

    """

    #: Assert ATN line synchronously (in 488 terminology). If a data handshake
    #: is in progress, ATN will not be asserted until the handshake is complete.
    asrt = VI_GPIB_ATN_ASSERT

    #: Assert ATN line asynchronously (in 488 terminology). This should generally
    #: be used only under error conditions.
    asrt_immediate = VI_GPIB_ATN_ASSERT_IMMEDIATE

    #: Deassert the ATN line
    deassert = VI_GPIB_ATN_DEASSERT

    #: Deassert ATN line, and enter shadow handshake mode. The local board will
    #: participate in data handshakes as an Acceptor without actually reading the data.
    deassert_handshake = VI_GPIB_ATN_DEASSERT_HANDSHAKE

@enum.unique
class RENLineOperation(enum.IntEnum):
"""Operation that can be performed on the REN line.

    Some operations apply to GPIB INSTR, GPIB INTFC, USB INSTR,
    TCPIP INSTR, please see the VISA reference for more details.

    """

    #: Send the Go To Local command (GTL) to this device.
    address_gtl = VI_GPIB_REN_ADDRESS_GTL

    #: Assert REN line.
    asrt = VI_GPIB_REN_ASSERT

    #: Assert REN line and address this device.
    asrt_address = VI_GPIB_REN_ASSERT_ADDRESS

    #: Address this device and send it LLO, putting it in RWLS
    asrt_address_llo = VI_GPIB_REN_ASSERT_ADDRESS_LLO

    #: Send LLO to any devices that are addressed to listen.
    asrt_llo = VI_GPIB_REN_ASSERT_LLO

    #: Deassert REN line.
    deassert = VI_GPIB_REN_DEASSERT

    #: Send the Go To Local command (GTL) to this device and deassert REN line.
    deassert_gtl = VI_GPIB_REN_DEASSERT_GTL

@enum.unique
class AddressSpace(enum.IntEnum):
"""Address space for register based resources."""

    #: A16 address space of VXI/MXI bus.
    a16 = VI_A16_SPACE

    #: A24 address space of VXI/MXI bus.
    a24 = VI_A24_SPACE

    #: A32 address space of VXI/MXI bus.
    a32 = VI_A32_SPACE

    #: A64 address space of VXI/MXI bus.
    a64 = VI_A64_SPACE

    #: PCI configuration space.
    pxi_config = VI_PXI_CFG_SPACE

    #: Specified PCI memory or I/O space
    pxi_bar0 = VI_PXI_BAR0_SPACE
    pxi_bar1 = VI_PXI_BAR1_SPACE
    pxi_bar2 = VI_PXI_BAR2_SPACE
    pxi_bar3 = VI_PXI_BAR3_SPACE
    pxi_bar4 = VI_PXI_BAR4_SPACE
    pxi_bar5 = VI_PXI_BAR5_SPACE

    #: Physical locally allocated memory.
    pxi_allocated = VI_PXI_ALLOC_SPACE

@enum.unique
class AddressModifiers(enum.IntEnum):
"""Address modifier to be used in high-level register operations."""

    data_private = VI_DATA_PRIV
    data_non_private = VI_DATA_NPRIV
    program_private = VI_PROG_PRIV
    program_non_private = VI_PROG_NPRIV
    block_private = VI_BLCK_PRIV
    block_non_private = VI_BLCK_NPRIV
    d64_private = VI_D64_PRIV
    d64_non_private = VI_D64_NPRIV
    d64_2vme = VI_D64_2EVME
    d64_sst160 = VI_D64_SST160
    d64_sst267 = VI_D64_SST267
    d64_sst320 = VI_D64_SST320

@enum.unique
class AssertSignalInterrupt(enum.IntEnum):
"""Line on which to perform an assertion or interrupt.

    Used only for VXI backplane and servant resources.

    """

    #: Use a VXI signal
    signal = VI_ASSERT_SIGNAL

    #: Use the mechanism specified in the response of Asynchronous Mode Control
    #: command. (VXI SERVANT only)
    use_assigned = VI_ASSERT_USE_ASSIGNED

    #: Send the interrupt via the specified VXI/VME IRQ line
    irq1 = VI_ASSERT_IRQ1
    irq2 = VI_ASSERT_IRQ2
    irq3 = VI_ASSERT_IRQ3
    irq4 = VI_ASSERT_IRQ4
    irq5 = VI_ASSERT_IRQ5
    irq6 = VI_ASSERT_IRQ6
    irq7 = VI_ASSERT_IRQ7

@enum.unique
class UtilityBusSignal(enum.IntEnum):
"""Operation on the utility line of a VXI backplane or servant."""

    #: Assert the SYSRESET ie perform a HARD RESET on the whole VXI bus.
    sysrest = VI_UTIL_ASSERT_SYSRESET

    #: Assert the SYSFAIL line.
    sysfail_assert = VI_UTIL_ASSERT_SYSFAIL

    #: Deassert the SYSFAIL line.
    sysfail_deassert = VI_UTIL_DEASSERT_SYSFAIL

@enum.unique
class VXICommands(enum.IntEnum):
"""VXI commands that can be sent using the vxi_command_query."""

    #: Send a command fitting in a 16-bit integer
    command_16 = VI_VXI_CMD16

    #: Read a response fitting in a 16-bit integer
    response16 = VI_VXI_RESP16

    #: Send a command and read a response both fitting in a 16-bit integer
    command_response_16 = VI_VXI_CMD16_RESP16

    #: Send a command fitting in a 32-bit integer
    command_32 = VI_VXI_CMD32

    #: Read a response fitting in a 32-bit integer
    response32 = VI_VXI_RESP32

    #: Send a command and read a response both fitting in a 32-bit integer
    command_response_32 = VI_VXI_CMD32_RESP32

    #: Send a command (32-bit integer) and read a response (16-bit integer)
    command_32_response_16 = VI_VXI_CMD32_RESP16

@enum.unique
class PXIMemory(enum.IntEnum):
"""Memory type used in a PXI BAR."""

    none = VI_PXI_ADDR_NONE
    memory = VI_PXI_ADDR_MEM
    io = VI_PXI_ADDR_IO
    cfg = VI_PXI_ADDR_CFG

@enum.unique
class VXIClass(enum.IntEnum):
"""VXI-defined device class."""

    memory = VI_VXI_CLASS_MEMORY
    extended = VI_VXI_CLASS_EXTENDED
    message = VI_VXI_CLASS_MESSAGE
    register = VI_VXI_CLASS_REGISTER
    other = VI_VXI_CLASS_OTHER

@enum.unique
class TriggerProtocol(enum.IntEnum):
"""Trigger protocol used when assering a resource trigger."""

    # FIXME The VISA standard is not very detailed on those
    #: Default protocol.
    #: This is the only valid protocol for software trigger on ASRL, GPIB, USB
    #: and VXI resources
    default = VI_TRIG_PROT_DEFAULT

    #:
    on = VI_TRIG_PROT_ON

    #:
    off = VI_TRIG_PROT_OFF

    #: For VXI devices equivalent to default
    sync = VI_TRIG_PROT_SYNC

    #: On PXI resources used to reserve a line for triggering
    reserve = VI_TRIG_PROT_RESERVE

    #: On PXI resources used to unreserve a line for triggering
    unreserve = VI_TRIG_PROT_UNRESERVE

@enum.unique
class InputTriggerLine(enum.IntEnum):
"""Trigger lines which can be mapped to another line.

    VXI, PXI devices.

    """

    #: TTL trigger lines
    ttl0 = VI_TRIG_TTL0
    ttl1 = VI_TRIG_TTL1
    ttl2 = VI_TRIG_TTL2
    ttl3 = VI_TRIG_TTL3
    ttl4 = VI_TRIG_TTL4
    ttl5 = VI_TRIG_TTL5
    ttl6 = VI_TRIG_TTL6
    ttl7 = VI_TRIG_TTL7

    # PXI specific TTL trigger lines
    ttl8 = VI_TRIG_TTL8
    ttl9 = VI_TRIG_TTL9
    ttl10 = VI_TRIG_TTL10
    ttl11 = VI_TRIG_TTL11

    #: ECL trigger lines
    ecl0 = VI_TRIG_ECL0
    ecl1 = VI_TRIG_ECL1
    ecl2 = VI_TRIG_ECL2
    ecl3 = VI_TRIG_ECL3
    ecl4 = VI_TRIG_ECL4
    ecl5 = VI_TRIG_ECL5

    #: Panel IN trigger line
    panel = VI_TRIG_PANEL_IN

    #: VXI STAR trigger input lines
    slot1 = VI_TRIG_STAR_SLOT1
    slot2 = VI_TRIG_STAR_SLOT2
    slot3 = VI_TRIG_STAR_SLOT3
    slot4 = VI_TRIG_STAR_SLOT4
    slot5 = VI_TRIG_STAR_SLOT5
    slot6 = VI_TRIG_STAR_SLOT6
    slot7 = VI_TRIG_STAR_SLOT7
    slot8 = VI_TRIG_STAR_SLOT8
    slot9 = VI_TRIG_STAR_SLOT9
    slot10 = VI_TRIG_STAR_SLOT10
    slot11 = VI_TRIG_STAR_SLOT11
    slot12 = VI_TRIG_STAR_SLOT12

@enum.unique
class OutputTriggerLine(enum.IntEnum):
"""Trigger lines to which another line can be mapped to.

    VXI, PXI devices.

    """

    #: TTL trigger lines
    ttl0 = VI_TRIG_TTL0
    ttl1 = VI_TRIG_TTL1
    ttl2 = VI_TRIG_TTL2
    ttl3 = VI_TRIG_TTL3
    ttl4 = VI_TRIG_TTL4
    ttl5 = VI_TRIG_TTL5
    ttl6 = VI_TRIG_TTL6
    ttl7 = VI_TRIG_TTL7

    # PXI specific TTL trigger lines
    ttl8 = VI_TRIG_TTL8
    ttl9 = VI_TRIG_TTL9
    ttl10 = VI_TRIG_TTL10
    ttl11 = VI_TRIG_TTL11

    #: VXI ECL trigger lines
    ecl0 = VI_TRIG_ECL0
    ecl1 = VI_TRIG_ECL1
    ecl2 = VI_TRIG_ECL2
    ecl3 = VI_TRIG_ECL3
    ecl4 = VI_TRIG_ECL4
    ecl5 = VI_TRIG_ECL5

    #: VXI STAR trigger out lines
    vxi0 = VI_TRIG_STAR_VXI0
    vxi1 = VI_TRIG_STAR_VXI1
    vxi2 = VI_TRIG_STAR_VXI2

    #: Panel OUT trigger line
    panel = VI_TRIG_PANEL_OUT

    #: All trigger lines (used only when unmapping lines)
    all = VI_TRIG_ALL

@enum.unique
class TriggerID(enum.IntEnum):
"""Identifier of the currently active trigerring mechanism on a resource."""

    #: Trigger using a serial word
    serial_word = VI_TRIG_SW

    #: TTL trigger lines
    ttl0 = VI_TRIG_TTL0
    ttl1 = VI_TRIG_TTL1
    ttl2 = VI_TRIG_TTL2
    ttl3 = VI_TRIG_TTL3
    ttl4 = VI_TRIG_TTL4
    ttl5 = VI_TRIG_TTL5
    ttl6 = VI_TRIG_TTL6
    ttl7 = VI_TRIG_TTL7

    # PXI specific TTL trigger lines
    ttl8 = VI_TRIG_TTL8
    ttl9 = VI_TRIG_TTL9
    ttl10 = VI_TRIG_TTL10
    ttl11 = VI_TRIG_TTL11

    #: VXI ECL trigger lines
    ecl0 = VI_TRIG_ECL0
    ecl1 = VI_TRIG_ECL1
    ecl2 = VI_TRIG_ECL2
    ecl3 = VI_TRIG_ECL3
    ecl4 = VI_TRIG_ECL4
    ecl5 = VI_TRIG_ECL5

    #: VXI STAR trigger out lines
    vxi0 = VI_TRIG_STAR_VXI0
    vxi1 = VI_TRIG_STAR_VXI1
    vxi2 = VI_TRIG_STAR_VXI2

    #: FIXME No definition in the VISA standards
    instr = VI_TRIG_STAR_INSTR

@enum.unique
class TriggerEventID(enum.IntEnum):
"""Identifier of the triggering mechanism on which a trigger event was received."""

    #: TTL trigger lines
    ttl0 = VI_TRIG_TTL0
    ttl1 = VI_TRIG_TTL1
    ttl2 = VI_TRIG_TTL2
    ttl3 = VI_TRIG_TTL3
    ttl4 = VI_TRIG_TTL4
    ttl5 = VI_TRIG_TTL5
    ttl6 = VI_TRIG_TTL6
    ttl7 = VI_TRIG_TTL7

    # PXI specific TTL trigger lines
    ttl8 = VI_TRIG_TTL8
    ttl9 = VI_TRIG_TTL9
    ttl10 = VI_TRIG_TTL10
    ttl11 = VI_TRIG_TTL11

    #: VXI ECL trigger lines
    ecl0 = VI_TRIG_ECL0
    ecl1 = VI_TRIG_ECL1
    ecl2 = VI_TRIG_ECL2
    ecl3 = VI_TRIG_ECL3
    ecl4 = VI_TRIG_ECL4
    ecl5 = VI_TRIG_ECL5

    #: FIXME No definition in the VISA standards
    instr = VI_TRIG_STAR_INSTR

@enum.unique
class ByteOrder(enum.IntEnum):
"""Byte order in register data transfer."""

    big_endian = VI_BIG_ENDIAN
    little_endian = VI_LITTLE_ENDIAN

@enum.unique
class DataWidth(enum.IntEnum):
"""Word width used when transferring data to/from register based resources."""

    #: Transfer data using 1 byte word
    bit_8 = VI_WIDTH_8

    #: Transfer data using 2 byte word
    bit_16 = VI_WIDTH_16

    #: Transfer data using 4 byte word
    bit_32 = VI_WIDTH_32

    #: Transfer data using 8 byte word
    bit_64 = VI_WIDTH_64

    @classmethod
    def from_literal(cls, value: Literal[8, 16, 32, 64]) -> "DataWidth":
        """Convert a literal width in the proper enum value."""
        if value not in (8, 16, 32, 64):
            raise ValueError(
                f"Invalid datawidth {value} specified. Valid values are (8, 16, 32, 64"
            )
        return cls(value // 8)

# Status code

[docs]
@enum.unique
class StatusCode(enum.IntEnum):
"""Status codes that VISA driver-level operations can return."""

    #: The operation was aborted.
    error_abort = VI_ERROR_ABORT

    #: Insufficient system resources to perform necessary memory allocation.
    error_allocation = VI_ERROR_ALLOC

    #: The specified attribute is read-only.
    error_attribute_read_only = VI_ERROR_ATTR_READONLY

    #: Bus error occurred during transfer.
    error_bus_error = VI_ERROR_BERR

    #: Unable to deallocate the previously allocated data structures corresponding
    #: to this session or object reference.
    error_closing_failed = VI_ERROR_CLOSING_FAILED

    #: The connection for the specified session has been lost.
    error_connection_lost = VI_ERROR_CONN_LOST

    #: An error occurred while trying to open the specified file.
    #: Possible causes include an invalid path or lack of access rights.
    error_file_access = VI_ERROR_FILE_ACCESS

    #: An error occurred while performing I/O on the specified file.
    error_file_i_o = VI_ERROR_FILE_IO

    #: A handler is not currently installed for the specified event.
    error_handler_not_installed = VI_ERROR_HNDLR_NINSTALLED
