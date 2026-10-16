# VISA shell launch, help, discovery, open and timeout
Context: PyVISA introduction; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](events-and-visa-shell-index.md) / [VISA shell complete resource-attribute output](visa-shell-resource-attribute-output.md) / [VISA shell termchar settings and close](visa-shell-termination-settings.md)

## PyVISA Shell

### PyVISA Shell

The shell was brought into PyVISA from the [Lantz](https://lantz.readthedocs.org) Project. It provides a text based interface for working with instruments, and you can launch it from the command-line:

```console
pyvisa-shell

```

that will show something the following prompt:

```text
Welcome to the VISA shell. Type help or ? to list commands.

(visa)

```

Type `?` or `help` whenever you want the shell to show the available commands:

```text
(visa) help

Documented commands (type help <topic>):
========================================
EOF  attr  close  exit  help  list  open  query  read  timeout write

(visa) help list
List all connected resources.

```

Tab completion is also supported.

The most basic task is listing all connected devices:

```text
(visa) list
( 0) ASRL1::INSTR
( 1) ASRL2::INSTR
( 2) USB0::0x1AB1::0x0588::DS1K00005888::INSTR

```

Every device/port receives a number for later commands. Open comport 1 like this:

```text
(visa) open 0
ASRL1::INSTR has been opened.
You can talk to the device using "write", "read" or "query.
The default end of message is added to each message
(open) query *IDN?
Some Instrument, Some Company.

```

You can print timeout that is set for query/read operation:

```text
(open) timeout
Timeout: 2000ms

```

You can also set a different timeout, for instance 1500ms (1.5 sec):

```text
(open) timeout 1500
Done

```

