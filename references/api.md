# Constants, Resourcemanager

> Pyvisa reference. Original prose; identifiers preserved verbatim.

## Overview

Covers these areas: Constants module; API; Resource Manager.

## Constants module

### Constants module

Defines readable names for values passed to or returned by different functions.

*class *pyvisa.constants.AccessModes(value)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/constants.html#AccessModes)

Controls whether a resource is locked when a connection is opened, and which lock style is used.

exclusive_lock* = 1*

Requests an exclusive lock on the VISA resource.

no_lock* = 0*

Opens the VISA resource without requesting a lock.

shared_lock* = 2*

Requests a VISA resouce lock that multiple VISA sessions may share.

*class *pyvisa.constants.StopBits(value)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/constants.html#StopBits)

Specifies how many stop bits mark the end of a frame for a serial resource.

Applies only to ASRL resources.

one* = 10*

one_and_a_half* = 15*

two* = 20*

*class *pyvisa.constants.Parity(value)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/constants.html#Parity)

Selects the parity type for each frame sent or received during a serial session.

Applies only to ASRL resources.

even* = 2*

mark* = 3*

none* = 0*

odd* = 1*

space* = 4*

*class *pyvisa.constants.SerialTermination(value)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/constants.html#SerialTermination)

Lists the supported ways to terminate a serial transfer.

last_bit* = 1*

The transfer keeps the last bit unset until the final character is sent.

none* = 0*

The transfer stops after all requested data has moved, or earlier if an error occurs.

termination_break* = 3*

After the write sends all characters, it transmits a break.

termination_char* = 2*

Termination happens by searching for "/" and appending the termination character.

*class *pyvisa.constants.InterfaceType(value)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/constants.html#InterfaceType)

Identifies the hardware interface.

asrl* = 4*

Serial devices attached through an RS-232 or RS-485 controller.

firewire* = 9*

Firewire device type.

gpib* = 1*

GPIB Interface type.

gpib_vxi* = 3*

GPIB VXI, meaning VME eXtensions for Instrumentation.

prlgx_asrl* = 34567*

prologix usb interface.

prlgx_tcpip* = 76543*

prologix tcpip interface.

pxi* = 5*

PXI device type.

rio* = 8*

Rio device type.

rsnrp* = 33024*

Rohde and Schwarz Device reached through Passport

tcpip* = 6*

TCPIP device type.

unknown* = -1*

usb* = 7*

Universal Serial Bus (USB) hardware bus type.

vicp* = 36000*

Lecroy VICP reached through passport

vxi* = 2*

VXI (VME eXtensions for Instrumentation), VME, or MXI (Multisystem eXtension Interface).

*class *pyvisa.constants.AddressState(value)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/constants.html#AddressState)

Describes a GPIB resource state.

Maps to the Attribute.GPIB_address_state attribute

listenr* = 2*

The resource has been addressed to listen

talker* = 1*

The resource has been addressed to talk

unaddressed* = 0*

The resource is unadressed

*class *pyvisa.constants.IOProtocol(value)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/constants.html#IOProtocol)

Communication IO protocol selection.

For more information, see attributes.AttrVI_ATTR_IO_PROT.

fdc* = 2*

Fast data channel (FDC) protocol used with VXI

hs488* = 3*

High speed 488 transfer mode for GPIB

normal* = 1*

protocol4882_strs* = 4*

488 style transfer mode for serial

usbtmc_vendor* = 5*

Vendor-specific test measurement class mode for USB

*class *pyvisa.constants.LineState(value)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/constants.html#LineState)

Represents the state of a hardware line or signal.

Queryable states include these lines: - ASRC resource signals: BREAK, CTS, DCD, DSR, DTR, RI, RTS - GPIB resources lines: ATN, NDAC, REN, SRQ - VXI BACKPLANE line: VXI/VME SYSFAIL backplane line

For additional details, search for LineState in attributes.py.

asserted* = 1*

The line/signal is asserted at this moment

unasserted* = 0*

The line/signal is deasserted at this moment

unknown* = -1*

The line/signal state is unknown

*class *pyvisa.constants.StatusCode(value)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/constants.html#StatusCode)

Status codes returned by VISA driver-level operations.

error_abort* = -1073807312*

The operation ended because it was aborted.

error_allocation* = -1073807300*

The system does not have enough resources for the required memory allocation.

error_attribute_read_only* = -1073807329*

The requested attribute cannot be modified because it is read-only.

error_bus_error* = -1073807304*

A bus error happened during the transfer.

error_closing_failed* = -1073807338*

The previously allocated data structures for this session or object reference could not be deallocated.

error_connection_lost* = -1073807194*

The connection associated with the specified session is no longer available.

error_file_access* = -1073807199*

Opening the specified file failed. Possible reasons include an invalid path or missing access rights.

error_file_i_o* = -1073807198*

An I/O operation on the specified file failed.

error_handler_not_installed* = -1073807320*

No handler is currently installed for the specified event.

error_in_progress* = -1073807303*

The asynchronous operation cannot be queued while another operation is already in progress.

error_input_protocol_violation* = -1073807305*

The device reported an input protocol error while the transfer was running.

error_interface_number_not_configured* = -1073807195*

The interface type is valid, but the requested interface number has not been configured.

error_interrupt_pending* = -1073807256*

A previous call left an interrupt pending.

error_invalid_access_key* = -1073807327*

The access key for the resource tied to this session is invalid.

error_invalid_access_mode* = -1073807341*

The access mode is invalid.

error_invalid_address_space* = -1073807282*

The specified address space is invalid.

error_invalid_context* = -1073807318*

The specified event context is invalid.

error_invalid_degree* = -1073807333*

The specified degree is invalid.

error_invalid_event* = -1073807322*

The resource does not support the specified event type.

error_invalid_expression* = -1073807344*

The search expression is invalid.

error_invalid_format* = -1073807297*

One format specifier in the format string is invalid.

error_invalid_handler_reference* = -1073807319*

The requested handler reference is invalid.

error_invalid_job_i_d* = -1073807332*

The specified job identifier is invalid.

error_invalid_length* = -1073807229*

The specified length is invalid.

error_invalid_line* = -1073807200*

The line parameter contains an invalid value.

error_invalid_lock_type* = -1073807328*

This resource does not support the specified lock type.

error_invalid_mask* = -1073807299*

The specified buffer mask is invalid.

error_invalid_mechanism* = -1073807321*

The specified mechanism is invalid.

error_invalid_mode* = -1073807215*

The specified mode is invalid.

error_invalid_object* = -1073807346*

The specified session or object reference is invalid.

error_invalid_offset* = -1073807279*

The specified offset is invalid.

error_invalid_parameter* = -1073807240*

An unknown parameter has an invalid value.

error_invalid_protocol* = -1073807239*

The specified protocol is invalid.

error_invalid_resource_name* = -1073807342*

The specified resource reference is invalid; parsing failed.

error_invalid_setup* = -1073807302*

The operation cannot start because setup is invalid from inconsistent property state.

error_invalid_size* = -1073807237*

The specified window size is invalid.

error_invalid_width* = -1073807278*

The specified source or destination width is invalid.

error_io* = -1073807298*

The operation could not run because an I/O error occurred.

error_library_not_found* = -1073807202*

VISA could not find or load a required code library.

error_line_in_use* = -1073807294*

The specified trigger line is already in use.

error_machine_not_available* = -1073807193*

The remote machine either does not exist or is refusing connections.

error_memory_not_shared* = -1073807203*

The device exports no memory.

error_no_listeners* = -1073807265*

A no listeners condition was detected because both NRFD and NDAC are deasserted.

error_no_permission* = -1073807192*

The remote machine denied access.

error_nonimplemented_operation* = -1073807231*

The requested operation has not been implemented.

error_nonsupported_attribute* = -1073807331*

The referenced session, event, or find list does not define or support the specified attribute.

error_nonsupported_attribute_state* = -1073807330*

The specified attribute state is invalid or unsupported for the session, event, or find list.

error_nonsupported_format* = -1073807295*

One format specifier in the format string is unsupported.

error_nonsupported_interrupt* = -1073807201*

The interface cannot generate an interrupt at the requested level or with the requested statusID value.

error_nonsupported_line* = -1073807197*

This VISA implementation does not support the specified trigger source line (trigSrc), destination line (trigDest), or the chosen line combination as a valid mapping.

error_nonsupported_mechanism* = -1073807196*

The specified event type does not support that mechanism.

error_nonsupported_mode* = -1073807290*

This VISA implementation does not support the specified mode.

error_nonsupported_offset* = -1073807276*

This hardware cannot access the specified offset.

error_nonsupported_offset_alignment* = -1073807248*

The specified offset is not aligned correctly for the operation access width.

error_nonsupported_operation* = -1073807257*

This operation is unsupported by the session or object reference.

error_nonsupported_varying_widths* = -1073807275*

Different source and destination widths are not supported.

error_nonsupported_width* = -1073807242*

This hardware does not support the specified width.

error_not_cic* = -1073807264*

The interface tied to this session is not currently the Controller-in-Charge.

error_not_enabled* = -1073807313*

The session has to be enabled for the specified event type before it can receive those events.

error_not_system_controller* = -1073807263*

The interface tied to this session is not the system controller.

error_output_protocol_violation* = -1073807306*

The device reported an output protocol error during the transfer.

error_queue_error* = -1073807301*

The asynchronous operation could not be queued.

error_queue_overflow* = -1073807315*

The event queue for the specified type overflowed, usually because previous events were not closed.

error_raw_read_protocol_violation* = -1073807307*

A raw read protocol violation occurred during the transfer.

error_raw_write_protocol_violation* = -1073807308*

A raw write protocol violation occurred during the transfer.

error_resource_busy* = -1073807246*

The resource is valid, but VISA cannot access it right now.

error_resource_locked* = -1073807345*

The specified lock type cannot be acquired, or the requested operation cannot run, because the resource is locked.

error_resource_not_found* = -1073807343*

Location information is insufficient, or the device or resource is absent from the system.

error_response_pending* = -1073807271*

A prior response remains pending, which causes a multiple query error.

error_serial_framing* = -1073807253*

A framing error happened during the transfer.

error_serial_overrun* = -1073807252*

An overrun error happened during the transfer. The hardware received the next character before the previous one was read.

error_serial_parity* = -1073807254*

A parity error happened during the transfer.

error_session_not_locked* = -1073807204*

The current session held no lock on the resource.

error_srq_not_occurred* = -1073807286*

The session has not received a service request.

error_system_error* = -1073807360*

The system error is unknown.

error_timeout* = -1073807339*

The timeout elapsed before the operation finished.

error_trigger_not_mapped* = -1073807250*

The path from trigger source line (trigSrc) to destination line (trigDest) is not mapped right now.

error_user_buffer* = -1073807247*

One specified user buffer is invalid or inaccessible at the required size.

error_window_already_mapped* = -1073807232*

The specified session already has a mapped window.

error_window_not_mapped* = -1073807273*

The specified session is unmapped right now.

success* = 0*

The operation finished successfully.

success_device_not_present* = 1073676413*

The session opened successfully, but the device at the specified address does not respond.

success_event_already_disabled* = 1073676291*

At least one of the specified mechanisms already has the specified event disabled.

success_event_already_enabled* = 1073676290*

At least one of the specified mechanisms already has the specified event enabled.

success_max_count_read* = 1073676294*

The byte count read matches the input count.

success_nested_exclusive* = 1073676442*

The operation finished successfully, and this session holds nested exclusive locks.

success_nested_shared* = 1073676441*

The operation finished successfully, and this session holds nested shared locks.

success_no_more_handler_calls_in_chain* = 1073676440*

The event was handled successfully. Do not call additional handlers on this session for this event.

success_queue_already_empty* = 1073676292*

The operation finished successfully, although the queue was already empty.

success_queue_not_empty* = 1073676416*

The wait ended successfully after an event notification arrived. At least one additional occurrence of the requested type(s) is still available for this session.

success_synchronous* = 1073676443*

The asynchronous operation request ran synchronously.

success_termination_character_read* = 1073676293*

The specified termination character has been read.

success_trigger_already_mapped* = 1073676414*

The path from trigger source line (trigSrc) to destination line (trigDest) is already mapped.

warning_configuration_not_loaded* = 1073676407*

The specified configuration is missing or could not load, so the VISA-specified defaults are used.

warning_ext_function_not_implemented* = 1073676457*

The operation succeeded, but a lower level driver lacks the extended functionality.

warning_nonsupported_attribute_state* = 1073676420*

The specified attribute state is valid, but this resource implementation does not support it.

warning_nonsupported_buffer* = 1073676424*

The specified buffer is unsupported.

warning_null_object* = 1073676418*

The specified object reference has not been initialized.

warning_queue_overflow* = 1073676300*

The configured queue could not contain all event information of the specified type received by VISA.

warning_unknown_status* = 1073676421*

The status code supplied to the operation could not be interpreted.

## API

### API

- [Visa Library](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html)
- [Resource Manager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html)
- [Resource classes](https://pyvisa.readthedocs.io/en/latest/api/resources.html)
- [Constants module](https://pyvisa.readthedocs.io/en/latest/api/constants.html)

## Resource Manager
