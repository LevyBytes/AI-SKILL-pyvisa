# User guide
Context: PyVISA introduction; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](events-and-visa-shell-index.md)

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

