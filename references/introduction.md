# Event Handling, Shell

> Pyvisa reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: User guide; Event handling; PyVISA Shell.

## User guide

### User guide

This user-guide section introduces the practical path into PyVISA. Later parts explain installing and configuring the library, talking to an instrument, and troubleshooting common communication problems.

- [Installation](https://pyvisa.readthedocs.io/en/latest/introduction/getting.html)
  - [Backend](https://pyvisa.readthedocs.io/en/latest/introduction/getting.html#backend)
  - [Testing your installation](https://pyvisa.readthedocs.io/en/latest/introduction/getting.html#testing-your-installation)
  - [Using the development version](https://pyvisa.readthedocs.io/en/latest/introduction/getting.html#using-the-development-version)

- [Configuring the backend](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html)
  - [Configuring the IVI backend](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html#configuring-the-ivi-backend)

- [Communicating with your instrument](https://pyvisa.readthedocs.io/en/latest/introduction/communication.html)
  - [An example](https://pyvisa.readthedocs.io/en/latest/introduction/communication.html#an-example)
  - [Getting the instrument configuration right](https://pyvisa.readthedocs.io/en/latest/introduction/communication.html#getting-the-instrument-configuration-right)

- [A more complex example](https://pyvisa.readthedocs.io/en/latest/introduction/example.html)
- [Reading and Writing values](https://pyvisa.readthedocs.io/en/latest/introduction/rvalues.html)
  - [Reading ASCII values](https://pyvisa.readthedocs.io/en/latest/introduction/rvalues.html#reading-ascii-values)
  - [Reading binary values](https://pyvisa.readthedocs.io/en/latest/introduction/rvalues.html#reading-binary-values)
  - [Writing ASCII values](https://pyvisa.readthedocs.io/en/latest/introduction/rvalues.html#writing-ascii-values)
  - [Writing binary values](https://pyvisa.readthedocs.io/en/latest/introduction/rvalues.html#writing-binary-values)
  - [When things are not what they should be](https://pyvisa.readthedocs.io/en/latest/introduction/rvalues.html#when-things-are-not-what-they-should-be)

- [Event handling](https://pyvisa.readthedocs.io/en/latest/introduction/event_handling.html)
  - [Waiting on events using a queue](https://pyvisa.readthedocs.io/en/latest/introduction/event_handling.html#waiting-on-events-using-a-queue)
  - [Registering handlers for event](https://pyvisa.readthedocs.io/en/latest/introduction/event_handling.html#registering-handlers-for-event)

- [Resources](https://pyvisa.readthedocs.io/en/latest/introduction/resources.html)
  - [Attributes of Resource](https://pyvisa.readthedocs.io/en/latest/introduction/resources.html#attributes-of-resource)
  - [Attributes of MessageBase resources](https://pyvisa.readthedocs.io/en/latest/introduction/resources.html#attributes-of-messagebase-resources)
  - [VISA attributes](https://pyvisa.readthedocs.io/en/latest/introduction/resources.html#visa-attributes)

- [PyVISA Shell](https://pyvisa.readthedocs.io/en/latest/introduction/shell.html)
  - [PyVisa Shell Backends](https://pyvisa.readthedocs.io/en/latest/introduction/shell.html#pyvisa-shell-backends)
  - [PyVisa Info](https://pyvisa.readthedocs.io/en/latest/introduction/shell.html#pyvisa-info)
  - [Summary](https://pyvisa.readthedocs.io/en/latest/introduction/shell.html#summary)

- [VISA resource names](https://pyvisa.readthedocs.io/en/latest/introduction/names.html)
  - [VISA Resource Syntax and Examples](https://pyvisa.readthedocs.io/en/latest/introduction/names.html#visa-resource-syntax-and-examples)

## Event handling

### Event handling

With VISA, an instrument can emit events, most often after a register changes, and the controller can process them through either of two mechanisms:

-

storing the events in a queue

-

invoking a handler function that was registered for the event when that event is raised

PyVISA can use both mechanisms and exposes a practical interface for each one. The examples below show the two approaches with a fictional instrument.

### Waiting on events using a queue

Start by looking at the queue-based pattern, where the code waits until an event has been placed in a queue.

```python
from pyvisa import ResourceManager, constants

rm = ResourceManager

with rm.open_resource("TCPIP::192.168.0.2::INSTR") as instr:

    # Type of event we want to be notified about
    event_type = constants.EventType.service_request
    # Mechanism by which we want to be notified
    event_mech = constants.EventMechanism.queue

    instr.enable_event(event_type, event_mech)

    # Instrument specific code to enable service request
    # (for example on operation complete OPC)
    instr.write("*SRE 1")
    instr.write("INIT")

    # Wait for the event to occur
    response = instr.wait_on_event(event_type, 1000)
    assert response.event.event_type == event_type
    assert response.timed_out = False
    instr.disable_event(event_type, event_mech)

```

Review the setup first: to avoid duplicating values, the code saves the desired event type and notification mechanism, then turns event notifications on.

```python
# Type of event we want to be notified about
event_type = constants.EventType.service_request
# Mechanism by which we want to be notified
event_mech = constants.EventMechanism.queue

instr.enable_event(event_type, event_mech)

```

The instrument must then be configured to emit the selected event at the appropriate moment, and the operation that will trigger it must be started. In this example the event is a Service Request event. Service requests are typically enabled for particular register states, with the exact details set by the instrument. Here, the useful case being modeled is a service request raised when an operation has finished.

Last, the code waits for the event and uses a timeout of 1000ms so it cannot block indefinitely. After the event arrives, event handling is disabled.

### Registering handlers for event

Instead of blocking until an event arrives, some workflows should react as soon as the event is raised; for those cases, direct invocation of a function by the VISA library is useful. Here is the pattern.

Note

One can enable event handling using both mechanisms (`constants.EventMechanism.all`)

```python
from time import sleep
from pyvisa import ResourceManager, constants

rm = ResourceManager

def handle_event(resource, event, user_handle):
    resource.called = True
    print(f"Handled event {event.event_type} on {resource}")

with rm.open_resource("TCPIP::192.168.0.2::INSTR") as instr:

    instr.called = False

    # Type of event we want to be notified about
    event_type = constants.EventType.service_request
    # Mechanism by which we want to be notified
    event_mech = constants.EventMechanism.handler

    wrapped = instr.wrap_handler(handle_event)

    user_handle = instr.install_handler(event_type, wrapped, 42)
    instr.enable_event(event_type, event_mech, None)

    # Instrument specific code to enable service request
    # (for example on operation complete OPC)
    instr.write("*SRE 1")
    instr.write("INIT")

    while not instr.called:
        sleep(10)

    instr.disable_event(event_type, event_mech)
    instr.uninstall_handler(event_type, wrapped, user_handle)

```

A handler must use the signature VISA expects: (session, event_type, event_context, user_handle). That raw callback shape is awkward because it exposes low-level values such as session, the VISA resource ID, and event_context, which plays the corresponding role for events. To present a cleaner handler API, call [`wrap_handler`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource.wrap_handler) on the [`Resource`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource) instance. After wrapping, the function should use this signature: (resource, event, user_handle), matching the handler used here:

```python
def handle_event(resource, event, user_handle):
    resource.called = True
    print(f"Handled event {event.event_type} on {resource}")

```

And before installing the handler, we wrap it:

```python
wrapped = instr.wrap_handler(handle_event)

```

Wrap the handler with the same resource that will later receive the installation. Also keep the wrapped handler object, because that exact object is needed when removing the handler.

Next we install the handler and enable the event processing:

```python
user_handle = instr.install_handler(event_type, wrapped, 42)
instr.enable_event(event_type, event_mech, None)

```

While installing a handler, you may provide a user handle that is forwarded to the callback. The handle helps distinguish which registration fired when the same handler has been installed more than once on one resource. A backend may convert this value, so the value delivered to the callback can differ from the one originally registered, and its concrete representation is backend dependent. Keep the converted value returned by install handler so the handler can be removed later.

Note

For the ctwrapper included with PyVISA, the backend maps the value to a matching ctypes object, such as c_float for a float or c_int for an integer, etc

## PyVISA Shell

### PyVISA Shell

The shell was brought into PyVISA from the [Lantz](https://lantz.readthedocs.org) Project. It provides a text based interface for working with instruments, and you can launch it from the command-line:

```python
pyvisa-shell

```

that will show something the following prompt:

```python
Welcome to the VISA shell. Type help or ? to list commands.

(visa)

```

Type `?` or `help` whenever you want the shell to show the available commands:

```python
(visa) help

Documented commands (type help <topic>):
========================================
EOF  attr  close  exit  help  list  open  query  read  timeout write

(visa) help list
List all connected resources.

```

Tab completion is also supported.

The most basic task is listing all connected devices:

```python
(visa) list
( 0) ASRL1::INSTR
( 1) ASRL2::INSTR
( 2) USB0::0x1AB1::0x0588::DS1K00005888::INSTR

```

Every device/port receives a number for later commands. Open comport 1 like this:

```python
(visa) open 0
ASRL1::INSTR has been opened.
You can talk to the device using "write", "read" or "query.
The default end of message is added to each message
(open) query *IDN?
Some Instrument, Some Company.

```

You can print timeout that is set for query/read operation:

```python
(open) timeout
Timeout: 2000ms

```

You can also set a different timeout, for instance 1500ms (1.5 sec):

```python
(open) timeout 1500
Done

```

We can also get a list of all visa attributes:

```python
(open) attr
+-----------------------------+------------+----------------------------+-------------------------------------+
|          VISA name          |  Constant  |        Python name         |                 val                 |
+-----------------------------+------------+----------------------------+-------------------------------------+
| VI_ATTR_ASRL_ALLOW_TRANSMIT | 1073676734 |       allow_transmit       |                  1                  |
|    VI_ATTR_ASRL_AVAIL_NUM   | 1073676460 |      bytes_in_buffer       |                  0                  |
|      VI_ATTR_ASRL_BAUD      | 1073676321 |         baud_rate          |                 9600                |
|    VI_ATTR_ASRL_BREAK_LEN   | 1073676733 |        break_length        |                 250                 |
|   VI_ATTR_ASRL_BREAK_STATE  | 1073676732 |        break_state         |                  0                  |
|    VI_ATTR_ASRL_CONNECTED   | 1073676731 |                            |          VI_ERROR_NSUP_ATTR         |
|    VI_ATTR_ASRL_CTS_STATE   | 1073676462 |                            |                  0                  |
|    VI_ATTR_ASRL_DATA_BITS   | 1073676322 |         data_bits          |                  8                  |
|    VI_ATTR_ASRL_DCD_STATE   | 1073676463 |                            |                  0                  |
|  VI_ATTR_ASRL_DISCARD_NULL  | 1073676464 |        discard_null        |                  0                  |
|    VI_ATTR_ASRL_DSR_STATE   | 1073676465 |                            |                  0                  |
|    VI_ATTR_ASRL_DTR_STATE   | 1073676466 |                            |                  1                  |
|     VI_ATTR_ASRL_END_IN     | 1073676467 |         end_input          |                  2                  |
|     VI_ATTR_ASRL_END_OUT    | 1073676468 |                            |                  0                  |
|   VI_ATTR_ASRL_FLOW_CNTRL   | 1073676325 |                            |                  0                  |
|     VI_ATTR_ASRL_PARITY     | 1073676323 |           parity           |                  0                  |
|  VI_ATTR_ASRL_REPLACE_CHAR  | 1073676478 |        replace_char        |                  0                  |
|    VI_ATTR_ASRL_RI_STATE    | 1073676479 |                            |                  0                  |
|    VI_ATTR_ASRL_RTS_STATE   | 1073676480 |                            |                  1                  |
|    VI_ATTR_ASRL_STOP_BITS   | 1073676324 |         stop_bits          |                  10                 |
|    VI_ATTR_ASRL_WIRE_MODE   | 1073676735 |                            |                 128                 |
|    VI_ATTR_ASRL_XOFF_CHAR   | 1073676482 |         xoff_char          |                  19                 |
|    VI_ATTR_ASRL_XON_CHAR    | 1073676481 |          xon_char          |                  17                 |
|     VI_ATTR_DMA_ALLOW_EN    | 1073676318 |         allow_dma          |                  0                  |
|    VI_ATTR_FILE_APPEND_EN   | 1073676690 |                            |                  0                  |
|    VI_ATTR_INTF_INST_NAME   | 3221160169 |                            | ASRL1  (/dev/cu.Bluetooth-PDA-Sync) |
|       VI_ATTR_INTF_NUM      | 1073676662 |      interface_number      |                  1                  |
|      VI_ATTR_INTF_TYPE      | 1073676657 |                            |                  4                  |
|       VI_ATTR_IO_PROT       | 1073676316 |        io_protocol         |                  1                  |
|   VI_ATTR_MAX_QUEUE_LENGTH  | 1073676293 |                            |                  50                 |
|   VI_ATTR_RD_BUF_OPER_MODE  | 1073676330 |                            |                  3                  |
|     VI_ATTR_RD_BUF_SIZE     | 1073676331 |                            |                 4096                |
|      VI_ATTR_RM_SESSION     | 1073676484 |                            |               3160976               |
|      VI_ATTR_RSRC_CLASS     | 3221159937 |       resource_class       |                INSTR                |
|  VI_ATTR_RSRC_IMPL_VERSION  | 1073676291 |   implementation_version   |               5243392               |
|   VI_ATTR_RSRC_LOCK_STATE   | 1073676292 |         lock_state         |                  0                  |
|     VI_ATTR_RSRC_MANF_ID    | 1073676661 |                            |                 4086                |
|    VI_ATTR_RSRC_MANF_NAME   | 3221160308 | resource_manufacturer_name |         National Instruments        |
|      VI_ATTR_RSRC_NAME      | 3221159938 |       resource_name        |             ASRL1::INSTR            |
|  VI_ATTR_RSRC_SPEC_VERSION  | 1073676656 |        spec_version        |               5243136               |
|     VI_ATTR_SEND_END_EN     | 1073676310 |          send_end          |                  1                  |
|   VI_ATTR_SUPPRESS_END_EN   | 1073676342 |                            |                  0                  |
|       VI_ATTR_TERMCHAR      | 1073676312 |                            |                  10                 |
|     VI_ATTR_TERMCHAR_EN     | 1073676344 |                            |                  0                  |
|      VI_ATTR_TMO_VALUE      | 1073676314 |                            |                 2000                |
|       VI_ATTR_TRIG_ID       | 1073676663 |                            |                  -1                 |
|   VI_ATTR_WR_BUF_OPER_MODE  | 1073676333 |                            |                  2                  |
|     VI_ATTR_WR_BUF_SIZE     | 1073676334 |                            |                 4096                |
+-----------------------------+------------+----------------------------+-------------------------------------+

```

The termchar command simplifies working with VI_ATTR_TERMCHAR and VI_ATTR_TERMCHAR_EN. Supplying one character applies that character to both read and write termination. Supplying two characters configures the read and write termination characters separately.

To setup termchar to ‘r’ (CR or ascii code 10):

```python
(open) termchar CR
Done

```

To read what termchar is defined:

```python
(open) termchar
Termchar read: CR write: CR

```

To setup read termchar to ‘n’ and write termchar to ‘rn':

```python
(open) termchar LF CRLF
Done

```

Accepted termchar settings are CR ('r'), LF ('n'), CRLF ('rn') , NUL ('0'), and None. Use None when termchar should be disabled.

Finally, you can close the device:

```python
(open) close

```

### PyVisa Shell Backends

If the desired backend is available (check with the `info` command), the shell can be switched away from the default backend using `-b BACKEND` or `--backend BACKEND`.

You can invoke:

```python
pyvisa-shell -b sim

```

This selects python-sim rather than the ni backend, which is useful when testing a python-sim configuration.

You can include a specific file to use for the simulated backend:

```python
pyvisa-shell -b file.yaml@sim

```

You can invoke:

```python
pyvisa-shell -b py

```

This selects python-py instead of the ivi backend for cases where ivi is not installed.

### PyVisa Info

You can invoke it from the command-line:

```python
pyvisa-info

```

This prints diagnostic information for PyVISA, including Machine, Python, backends, etc

```python
Machine Details:
   Platform ID:    Windows
   Processor:      Intel64 Family 6
   ...
PyVISA Version: ...

Backends:
   ni:
      Version: 1.8 (bundled with PyVISA)
      ...
   py:
      Version: 0.2
      ...
  sim:
     Version: 0.3
     Spec version: 1.1

```

### Summary

Useful, yes? A GUI in the style of NI-MAX would be nice, but that work is left outside PyVISA. Want to help? Let us know!
