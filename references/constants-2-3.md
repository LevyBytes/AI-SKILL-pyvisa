# Constants (part 2) (3)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

    #: Unable to queue the asynchronous operation because there is already
    #: an operation in progress.
    error_in_progress = VI_ERROR_IN_PROGRESS

    #: Device reported an input protocol error during transfer.
    error_input_protocol_violation = VI_ERROR_INP_PROT_VIOL

    #: The interface type is valid but the specified interface number is not configured.
    error_interface_number_not_configured = VI_ERROR_INTF_NUM_NCONFIG

    #: An interrupt is still pending from a previous call.
    error_interrupt_pending = VI_ERROR_INTR_PENDING

    #: The access key to the resource associated with this session is invalid.
    error_invalid_access_key = VI_ERROR_INV_ACCESS_KEY

    #: Invalid access mode.
    error_invalid_access_mode = VI_ERROR_INV_ACC_MODE

    #: Invalid address space specified.
    error_invalid_address_space = VI_ERROR_INV_SPACE

    #: Specified event context is invalid.
    error_invalid_context = VI_ERROR_INV_CONTEXT

    #: Specified degree is invalid.
    error_invalid_degree = VI_ERROR_INV_DEGREE

    #: Specified event type is not supported by the resource.
    error_invalid_event = VI_ERROR_INV_EVENT

    #: Invalid expression specified for search.
    error_invalid_expression = VI_ERROR_INV_EXPR

    #: A format specifier in the format string is invalid.
    error_invalid_format = VI_ERROR_INV_FMT

    #: The specified handler reference is invalid.
    error_invalid_handler_reference = VI_ERROR_INV_HNDLR_REF

    #: Specified job identifier is invalid.
    error_invalid_job_i_d = VI_ERROR_INV_JOB_ID

    #: Invalid length specified.
    error_invalid_length = VI_ERROR_INV_LENGTH

    #: The value specified by the line parameter is invalid.
    error_invalid_line = VI_ERROR_INV_LINE

    #: The specified type of lock is not supported by this resource.
    error_invalid_lock_type = VI_ERROR_INV_LOCK_TYPE

    #: Invalid buffer mask specified.
    error_invalid_mask = VI_ERROR_INV_MASK

    #: Invalid mechanism specified.
    error_invalid_mechanism = VI_ERROR_INV_MECH

    #: The specified mode is invalid.
    error_invalid_mode = VI_ERROR_INV_MODE

    #: The specified session or object reference is invalid.
    error_invalid_object = VI_ERROR_INV_OBJECT

    #: Invalid offset specified.
    error_invalid_offset = VI_ERROR_INV_OFFSET

    #: The value of an unknown parameter is invalid.
    error_invalid_parameter = VI_ERROR_INV_PARAMETER

    #: The protocol specified is invalid.
    error_invalid_protocol = VI_ERROR_INV_PROT

    #: Invalid resource reference specified. Parsing error.
    error_invalid_resource_name = VI_ERROR_INV_RSRC_NAME

    #: Unable to start operation because setup is invalid due to inconsistent
    #: state of properties.
    error_invalid_setup = VI_ERROR_INV_SETUP

    #: Invalid size of window specified.
    error_invalid_size = VI_ERROR_INV_SIZE

    #: Invalid source or destination width specified.
    error_invalid_width = VI_ERROR_INV_WIDTH

    #: Could not perform operation because of I/O error.
    error_io = VI_ERROR_IO

    #: A code library required by VISA could not be located or loaded.
    error_library_not_found = VI_ERROR_LIBRARY_NFOUND

    #: The specified trigger line is currently in use.
    error_line_in_use = VI_ERROR_LINE_IN_USE

    #: The remote machine does not exist or is not accepting any connections.
    error_machine_not_available = VI_ERROR_MACHINE_NAVAIL

    #: The device does not export any memory.
    error_memory_not_shared = VI_ERROR_MEM_NSHARED

    #: No listeners condition is detected (both NRFD and NDAC are deasserted).
    error_no_listeners = VI_ERROR_NLISTENERS

    #: The specified operation is unimplemented.
    error_nonimplemented_operation = VI_ERROR_NIMPL_OPER

    #: The specified attribute is not defined or supported by the referenced
    #: session, event, or find list.
    error_nonsupported_attribute = VI_ERROR_NSUP_ATTR

    #: The specified state of the attribute is not valid or is not supported as
    #: defined by the session, event, or find list.
    error_nonsupported_attribute_state = VI_ERROR_NSUP_ATTR_STATE

    #: A format specifier in the format string is not supported.
    error_nonsupported_format = VI_ERROR_NSUP_FMT

    #: The interface cannot generate an interrupt on the requested level or with
    #: the requested statusID value.
    error_nonsupported_interrupt = VI_ERROR_NSUP_INTR

    #: The specified trigger source line (trigSrc) or destination line (trigDest)
    #: is not supported by this VISA implementation, or the combination of lines
    #: is not a valid mapping.
    error_nonsupported_line = VI_ERROR_NSUP_LINE

    #: The specified mechanism is not supported for the specified event type.
    error_nonsupported_mechanism = VI_ERROR_NSUP_MECH

    #: The specified mode is not supported by this VISA implementation.
    error_nonsupported_mode = VI_ERROR_NSUP_MODE

    #: Specified offset is not accessible from this hardware.
    error_nonsupported_offset = VI_ERROR_NSUP_OFFSET

    #: The specified offset is not properly aligned for the access width of
    #: the operation.
    error_nonsupported_offset_alignment = VI_ERROR_NSUP_ALIGN_OFFSET

    #: The session or object reference does not support this operation.
    error_nonsupported_operation = VI_ERROR_NSUP_OPER

    #: Cannot support source and destination widths that are different.
    error_nonsupported_varying_widths = VI_ERROR_NSUP_VAR_WIDTH

    #: Specified width is not supported by this hardware.
    error_nonsupported_width = VI_ERROR_NSUP_WIDTH

    #: Access to the remote machine is denied.
    error_no_permission = VI_ERROR_NPERMISSION

    #: The interface associated with this session is not currently the
    #: Controller-in-Charge.
    error_not_cic = VI_ERROR_NCIC

    #: The session must be enabled for events of the specified type in order to
    #: receive them.
    error_not_enabled = VI_ERROR_NENABLED

    #: The interface associated with this session is not the system controller.
    error_not_system_controller = VI_ERROR_NSYS_CNTLR

    #: Device reported an output protocol error during transfer.
    error_output_protocol_violation = VI_ERROR_OUTP_PROT_VIOL

    #: Unable to queue asynchronous operation.
    error_queue_error = VI_ERROR_QUEUE_ERROR

    #: The event queue for the specified type has overflowed, usually due to
    #: not closing previous events.
    error_queue_overflow = VI_ERROR_QUEUE_OVERFLOW

    #: Violation of raw read protocol occurred during transfer.
    error_raw_read_protocol_violation = VI_ERROR_RAW_RD_PROT_VIOL

    #: Violation of raw write protocol occurred during transfer.
    error_raw_write_protocol_violation = VI_ERROR_RAW_WR_PROT_VIOL

    #: The resource is valid, but VISA cannot currently access it.
    error_resource_busy = VI_ERROR_RSRC_BUSY

    #: Specified type of lock cannot be obtained or specified operation cannot
    #: be performed because the resource is locked.
    error_resource_locked = VI_ERROR_RSRC_LOCKED

    #: Insufficient location information, or the device or resource is not
    #: present in the system.
    error_resource_not_found = VI_ERROR_RSRC_NFOUND

    #: A previous response is still pending, causing a multiple query error.
    error_response_pending = VI_ERROR_RESP_PENDING

    #: A framing error occurred during transfer.
    error_serial_framing = VI_ERROR_ASRL_FRAMING

    #: An overrun error occurred during transfer. A character was not read from
    #: the hardware before the next character arrived.
    error_serial_overrun = VI_ERROR_ASRL_OVERRUN

    #: A parity error occurred during transfer.
    error_serial_parity = VI_ERROR_ASRL_PARITY

    #: The current session did not have any lock on the resource.
    error_session_not_locked = VI_ERROR_SESN_NLOCKED

    #: Service request has not been received for the session.
    error_srq_not_occurred = VI_ERROR_SRQ_NOCCURRED

    #: Unknown system error.
    error_system_error = VI_ERROR_SYSTEM_ERROR

    #: Timeout expired before operation completed.
    error_timeout = VI_ERROR_TMO

    #: The path from the trigger source line (trigSrc) to the destination line
    #: (trigDest) is not currently mapped.
    error_trigger_not_mapped = VI_ERROR_TRIG_NMAPPED

    #: A specified user buffer is not valid or cannot be accessed for the
    #: required size.
    error_user_buffer = VI_ERROR_USER_BUF

    #: The specified session currently contains a mapped window.
    error_window_already_mapped = VI_ERROR_WINDOW_MAPPED

    #: The specified session is currently unmapped.
    error_window_not_mapped = VI_ERROR_WINDOW_NMAPPED

    #: Operation completed successfully.
    success = VI_SUCCESS

    #: Session opened successfully, but the device at the specified address is
    #: not responding.
    success_device_not_present = VI_SUCCESS_DEV_NPRESENT

    #: Specified event is already disabled for at least one of the specified mechanisms.
    success_event_already_disabled = VI_SUCCESS_EVENT_DIS

    #: Specified event is already enabled for at least one of the specified mechanisms.
    success_event_already_enabled = VI_SUCCESS_EVENT_EN

    #: The number of bytes read is equal to the input count.
    success_max_count_read = VI_SUCCESS_MAX_CNT

    #: Operation completed successfully, and this session has nested exclusive locks.
    success_nested_exclusive = VI_SUCCESS_NESTED_EXCLUSIVE

    #: Operation completed successfully, and this session has nested shared locks.
    success_nested_shared = VI_SUCCESS_NESTED_SHARED

    #: Event handled successfully. Do not invoke any other handlers on this session
    #: for this event.
    success_no_more_handler_calls_in_chain = VI_SUCCESS_NCHAIN

    #: Operation completed successfully, but the queue was already empty.
    success_queue_already_empty = VI_SUCCESS_QUEUE_EMPTY

    #: Wait terminated successfully on receipt of an event notification. There
    #: is still at least one more event occurrence of the requested type(s)
    #: available for this session.
    success_queue_not_empty = VI_SUCCESS_QUEUE_NEMPTY

    #: Asynchronous operation request was performed synchronously.
    success_synchronous = VI_SUCCESS_SYNC

    #: The specified termination character was read.
    success_termination_character_read = VI_SUCCESS_TERM_CHAR

    #: The path from the trigger source line (trigSrc) to the destination line
    #: (trigDest) is already mapped.
    success_trigger_already_mapped = VI_SUCCESS_TRIG_MAPPED

    #: The specified configuration either does not exist or could not be loaded.
    #: The VISA-specified defaults are used.
    warning_configuration_not_loaded = VI_WARN_CONFIG_NLOADED

    #: The operation succeeded, but a lower level driver did not implement the
    #: extended functionality.
    warning_ext_function_not_implemented = VI_WARN_EXT_FUNC_NIMPL

    #: Although the specified state of the attribute is valid, it is not supported
    #: by this resource implementation.
    warning_nonsupported_attribute_state = VI_WARN_NSUP_ATTR_STATE

    #: The specified buffer is not supported.
    warning_nonsupported_buffer = VI_WARN_NSUP_BUF

    #: The specified object reference is uninitialized.
    warning_null_object = VI_WARN_NULL_OBJECT

    #: VISA received more event information of the specified type than the
    #: configured queue size could hold.
    warning_queue_overflow = VI_WARN_QUEUE_OVERFLOW

    #: The status code passed to the operation could not be interpreted.
    warning_unknown_status = VI_WARN_UNKNOWN_STATUS

# --- Attributes -----------------------------------------------------------------------

@enum.unique
class EventAttribute(enum.IntEnum):
"""The possible attributes of VISA events."""

    event_type = VI_ATTR_EVENT_TYPE
    status = VI_ATTR_STATUS
    operation_name = VI_ATTR_OPER_NAME
    job_id = VI_ATTR_JOB_ID
    return_count = VI_ATTR_RET_COUNT
    buffer = VI_ATTR_BUFFER
    received_trigger_id = VI_ATTR_RECV_TRIG_ID
    gpib_received_cic_state = VI_ATTR_GPIB_RECV_CIC_STATE
    received_tcpip_connect = VI_ATTR_RECV_TCPIP_ADDR
    usb_received_interrupt_size = VI_ATTR_USB_RECV_INTR_SIZE
    usb_received_interrupt_data = VI_ATTR_USB_RECV_INTR_DATA
    signal_register_status_id = VI_ATTR_SIGP_STATUS_ID
    interrupt_status_id = VI_ATTR_INTR_STATUS_ID
    received_interrupt_level = VI_ATTR_RECV_INTR_LEVEL
    pxi_received_interrupt_sequence = VI_ATTR_PXI_RECV_INTR_SEQ
    pxi_received_interrupt_data = VI_ATTR_PXI_RECV_INTR_DATA

@enum.unique
class ResourceAttribute(enum.IntEnum):
"""The possible attributes of VISA resources."""

    # All sessions
    resource_manager_session = VI_ATTR_RM_SESSION
    interface_type = VI_ATTR_INTF_TYPE
    interface_number = VI_ATTR_INTF_NUM
    interface_instrument_name = VI_ATTR_INTF_INST_NAME
    resource_class = VI_ATTR_RSRC_CLASS
    resource_name = VI_ATTR_RSRC_NAME
    resource_impl_version = VI_ATTR_RSRC_IMPL_VERSION
    resource_lock_state = VI_ATTR_RSRC_LOCK_STATE
    resource_spec_version = VI_ATTR_RSRC_SPEC_VERSION
    resource_manufacturer_name = VI_ATTR_RSRC_MANF_NAME
    resource_manufacturer_id = VI_ATTR_RSRC_MANF_ID
    timeout_value = VI_ATTR_TMO_VALUE
    max_queue_length = VI_ATTR_MAX_QUEUE_LENGTH
    user_data = VI_ATTR_USER_DATA
    trigger_id = VI_ATTR_TRIG_ID  # most resources no USB, nor TCPIP::SOCKET

    # Message based resource attributes
    send_end_enabled = VI_ATTR_SEND_END_EN
    suppress_end_enabled = VI_ATTR_SUPPRESS_END_EN
    termchar_enabled = VI_ATTR_TERMCHAR_EN
    termchar = VI_ATTR_TERMCHAR
    io_prot = VI_ATTR_IO_PROT
    file_append_enabled = VI_ATTR_FILE_APPEND_EN
    read_buffer_operation_mode = VI_ATTR_RD_BUF_OPER_MODE
    read_buffer_size = VI_ATTR_RD_BUF_SIZE
    write_buffer_operation_mode = VI_ATTR_WR_BUF_OPER_MODE
    write_buffer_size = VI_ATTR_WR_BUF_SIZE

    dma_allow_enabled = VI_ATTR_DMA_ALLOW_EN

    # TCPIP specific attributes
    tcpip_address = VI_ATTR_TCPIP_ADDR
    tcpip_hostname = VI_ATTR_TCPIP_HOSTNAME
    tcpip_port = VI_ATTR_TCPIP_PORT
    tcpip_device_name = VI_ATTR_TCPIP_DEVICE_NAME
    tcpip_nodelay = VI_ATTR_TCPIP_NODELAY
    tcpip_keepalive = VI_ATTR_TCPIP_KEEPALIVE
    tcpip_is_hislip = VI_ATTR_TCPIP_IS_HISLIP
    tcpip_hislip_version = VI_ATTR_TCPIP_HISLIP_VERSION
    tcpip_hislip_overlap_enable = VI_ATTR_TCPIP_HISLIP_OVERLAP_EN
    tcpip_hislip_max_message_kb = VI_ATTR_TCPIP_HISLIP_MAX_MESSAGE_KB

    # GPIB specific attributes
    gpib_primary_address = VI_ATTR_GPIB_PRIMARY_ADDR
    gpib_secondary_address = VI_ATTR_GPIB_SECONDARY_ADDR
    gpib_system_controller = VI_ATTR_GPIB_SYS_CNTRL_STATE
    gpib_cic_state = VI_ATTR_GPIB_CIC_STATE
    gpib_ren_state = VI_ATTR_GPIB_REN_STATE
    gpib_atn_state = VI_ATTR_GPIB_ATN_STATE
    gpib_ndac_state = VI_ATTR_GPIB_NDAC_STATE
    gpib_srq_state = VI_ATTR_GPIB_SRQ_STATE
    gpib_address_state = VI_ATTR_GPIB_ADDR_STATE
    gpib_unadress_enable = VI_ATTR_GPIB_UNADDR_EN
    gpib_readdress_enabled = VI_ATTR_GPIB_READDR_EN
    gpib_hs488_cable_length = VI_ATTR_GPIB_HS488_CBL_LEN

    # Serial specific attributes
    asrl_avalaible_number = VI_ATTR_ASRL_AVAIL_NUM
    asrl_baud_rate = VI_ATTR_ASRL_BAUD
    asrl_data_bits = VI_ATTR_ASRL_DATA_BITS
    asrl_parity = VI_ATTR_ASRL_PARITY
    asrl_stop_bits = VI_ATTR_ASRL_STOP_BITS
    asrl_flow_control = VI_ATTR_ASRL_FLOW_CNTRL
    asrl_discard_null = VI_ATTR_ASRL_DISCARD_NULL
    asrl_connected = VI_ATTR_ASRL_CONNECTED
    asrl_allow_transmit = VI_ATTR_ASRL_ALLOW_TRANSMIT
    asrl_end_in = VI_ATTR_ASRL_END_IN
    asrl_end_out = VI_ATTR_ASRL_END_OUT
    asrl_break_length = VI_ATTR_ASRL_BREAK_LEN
    asrl_break_state = VI_ATTR_ASRL_BREAK_STATE
    asrl_replace_char = VI_ATTR_ASRL_REPLACE_CHAR
    asrl_xon_char = VI_ATTR_ASRL_XON_CHAR
    asrl_xoff_char = VI_ATTR_ASRL_XOFF_CHAR
    asrl_cts_state = VI_ATTR_ASRL_CTS_STATE
    asrl_dsr_state = VI_ATTR_ASRL_DSR_STATE
    asrl_dtr_state = VI_ATTR_ASRL_DTR_STATE
    asrl_rts_state = VI_ATTR_ASRL_RTS_STATE
    asrl_wire_mode = VI_ATTR_ASRL_WIRE_MODE
    asrl_dcd_state = VI_ATTR_ASRL_DCD_STATE
    asrl_ri_state = VI_ATTR_ASRL_RI_STATE

    # USB specific attributes
    usb_interface_number = VI_ATTR_USB_INTFC_NUM
    usb_serial_number = VI_ATTR_USB_SERIAL_NUM
    usb_protocol = VI_ATTR_USB_PROTOCOL
    usb_max_interrupt_size = VI_ATTR_USB_MAX_INTR_SIZE
    usb_class = VI_ATTR_USB_CLASS
    usb_subclass = VI_ATTR_USB_SUBCLASS
    usb_bulk_in_status = VI_ATTR_USB_BULK_IN_STATUS
    usb_bulk_in_pipe = VI_ATTR_USB_BULK_IN_PIPE
    usb_bulk_out_status = VI_ATTR_USB_BULK_OUT_STATUS
    usb_bulk_out_pipe = VI_ATTR_USB_BULK_OUT_PIPE
    usb_interrupt_in_pipe = VI_ATTR_USB_INTR_IN_PIPE
    usb_alt_setting = VI_ATTR_USB_ALT_SETTING
    usb_end_in = VI_ATTR_USB_END_IN
    usb_number_interfaces = VI_ATTR_USB_NUM_INTFCS
    usb_number_pipes = VI_ATTR_USB_NUM_PIPES
    usb_interrupt_in_status = VI_ATTR_USB_INTR_IN_STATUS
    usb_control_pipe = VI_ATTR_USB_CTRL_PIPE

    #  USB, VXI, GPIB-VXI, PXI specific attributes
    manufacturer_name = VI_ATTR_MANF_NAME
    manufacturer_id = VI_ATTR_MANF_ID
    model_name = VI_ATTR_MODEL_NAME
    model_code = VI_ATTR_MODEL_CODE

    # GPIB INTFC, VXI SERVANT
    device_status_byte = VI_ATTR_DEV_STATUS_BYTE

    #  (USB, VXI, GPIB-VXI)::INSTR specific attributes
    is_4882_compliant = VI_ATTR_4882_COMPLIANT

    # (VXI, GPIB-VXI and PXI)::INSTR specific attributes
    slot = VI_ATTR_SLOT
    window_access = VI_ATTR_WIN_ACCESS
    window_base_address = VI_ATTR_WIN_BASE_ADDR
    window_size = VI_ATTR_WIN_SIZE
    source_increment = VI_ATTR_SRC_INCREMENT
    destination_increment = VI_ATTR_DEST_INCREMENT

    # VXI and GPIB-VXI specific attributes
    fdc_channel = VI_ATTR_FDC_CHNL
    fdc_mode = VI_ATTR_FDC_MODE
    fdc_generate_signal_enabled = VI_ATTR_FDC_GEN_SIGNAL_EN
    fdc_use_pair = VI_ATTR_FDC_USE_PAIR
    mainframe_logical_address = VI_ATTR_MAINFRAME_LA
    vxi_logical_address = VI_ATTR_VXI_LA
    commander_logical_address = VI_ATTR_CMDR_LA
    memory_space = VI_ATTR_MEM_SPACE
    memory_size = VI_ATTR_MEM_SIZE
    memory_base = VI_ATTR_MEM_BASE
    immediate_servant = VI_ATTR_IMMEDIATE_SERV
    destination_access_private = VI_ATTR_DEST_ACCESS_PRIV
    destination_byte_order = VI_ATTR_DEST_BYTE_ORDER
    source_access_private = VI_ATTR_SRC_ACCESS_PRIV
    source_byte_order = VI_ATTR_SRC_BYTE_ORDER
    window_access_private = VI_ATTR_WIN_ACCESS_PRIV
    window_byte_order = VI_ATTR_WIN_BYTE_ORDER
    vxi_trigger_support = VI_ATTR_VXI_TRIG_SUPPORT

    # GPIB-VXI specific attributes
    interface_parent_number = VI_ATTR_INTF_PARENT_NUM

    # VXI specific attributes
    vxi_device_class = VI_ATTR_VXI_DEV_CLASS  # INSTR
    vxi_trig_dir = VI_ATTR_VXI_TRIG_DIR  # INSTR
    vxi_trig_lines_enabled = VI_ATTR_VXI_TRIG_LINES_EN  # INSTR
    vxi_vme_interrupt_status = VI_ATTR_VXI_VME_INTR_STATUS  # BACKPLANE
    vxi_trigger_status = VI_ATTR_VXI_TRIG_STATUS  # BACKPLANE
    vxi_vme_sysfail_state = VI_ATTR_VXI_VME_SYSFAIL_STATE  # BACKPLANE

    # PXI specific attributes
    pxi_device_number = VI_ATTR_PXI_DEV_NUM
    pxi_function_num = VI_ATTR_PXI_FUNC_NUM
    pxi_bus_number = VI_ATTR_PXI_BUS_NUM
    pxi_chassis = VI_ATTR_PXI_CHASSIS
    pxi_slotpath = VI_ATTR_PXI_SLOTPATH
    pxi_slot_lbus_left = VI_ATTR_PXI_SLOT_LBUS_LEFT
    pxi_slot_lbus_right = VI_ATTR_PXI_SLOT_LBUS_RIGHT
    pxi_is_express = VI_ATTR_PXI_IS_EXPRESS
    pxi_slot_lwidth = VI_ATTR_PXI_SLOT_LWIDTH
    pxi_max_ldwidth = VI_ATTR_PXI_MAX_LWIDTH
    pxi_actual_ldwidth = VI_ATTR_PXI_ACTUAL_LWIDTH
    pxi_dstar_bus = VI_ATTR_PXI_DSTAR_BUS
    pxi_dstar_set = VI_ATTR_PXI_DSTAR_SET
    pxi_trig_bus = VI_ATTR_PXI_TRIG_BUS
    pxi_star_trig_bus = VI_ATTR_PXI_STAR_TRIG_BUS
    pxi_star_trig_line = VI_ATTR_PXI_STAR_TRIG_LINE
    pxi_source_trigger_bus = VI_ATTR_PXI_SRC_TRIG_BUS
    pxi_destination_trigger_bus = VI_ATTR_PXI_DEST_TRIG_BUS

    # PXI BAR memory scpecific attributes
    pxi_memory_type_bar0 = VI_ATTR_PXI_MEM_TYPE_BAR0
    pxi_memory_type_bar1 = VI_ATTR_PXI_MEM_TYPE_BAR1
    pxi_memory_type_bar2 = VI_ATTR_PXI_MEM_TYPE_BAR2
    pxi_memory_type_bar3 = VI_ATTR_PXI_MEM_TYPE_BAR3
    pxi_memory_type_bar4 = VI_ATTR_PXI_MEM_TYPE_BAR4
    pxi_memory_type_bar5 = VI_ATTR_PXI_MEM_TYPE_BAR5

    pxi_memory_base_bar0 = VI_ATTR_PXI_MEM_BASE_BAR0
    pxi_memory_base_bar1 = VI_ATTR_PXI_MEM_BASE_BAR1
    pxi_memory_base_bar2 = VI_ATTR_PXI_MEM_BASE_BAR2
    pxi_memory_base_bar3 = VI_ATTR_PXI_MEM_BASE_BAR3
    pxi_memory_base_bar4 = VI_ATTR_PXI_MEM_BASE_BAR4
    pxi_memory_base_bar5 = VI_ATTR_PXI_MEM_BASE_BAR5
    pxi_memory_size_bar0 = VI_ATTR_PXI_MEM_SIZE_BAR0
    pxi_memory_size_bar1 = VI_ATTR_PXI_MEM_SIZE_BAR1
    pxi_memory_size_bar2 = VI_ATTR_PXI_MEM_SIZE_BAR2
    pxi_memory_size_bar3 = VI_ATTR_PXI_MEM_SIZE_BAR3
    pxi_memory_size_bar4 = VI_ATTR_PXI_MEM_SIZE_BAR4
    pxi_memory_size_bar5 = VI_ATTR_PXI_MEM_SIZE_BAR5

```

```
