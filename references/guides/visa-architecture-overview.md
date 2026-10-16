# General overview
Context: PyVISA latest; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](instrument-control-overview-index.md)

### General overview

Writing software to talk to measurement instruments is often a headache. A wide range of protocols travel across an equally wide range of interfaces and bus systems (e.g. GPIB, RS232, USB, Ethernet). Whatever language you choose, you must hunt down libraries that cover both your particular device and the bus it sits on.

To relieve that pain, the Virtual Instrument Software Architecture (VISA) specification was laid down around the middle of the 90ies. VISA gives a common way to set up, drive, and debug instrumentation built on GPIB, VXI, PXI, Serial, Ethernet, and/or USB interfaces.

These days every major operating system has a VISA implementation. Several vendors ship VISA libraries, some of them free to download. Such a library will cooperate with any peripheral you attach, though it might only support that vendor's own interface hardware, for instance their GPIB card.

The spec ships defined bindings for Visual Basic, C, and G (LabVIEW’s graphical language). From Python you can reach into a VISA shared library (.dll, .so, .dylib) and call those functions, putting the established implementations to work right away. Python is also capable of reaching most instrument bus systems on its own, so it is feasible to build out the VISA standard purely in Python (the PyVISA-Py project covers this). PyVISA fills both roles: it wraps VISA shared libraries, and it can equally act as a front-end over an alternative VISA implementation like PyVISA-Py.

- [User guide](https://pyvisa.readthedocs.io/en/latest/introduction/index.html)
  - [Installation](https://pyvisa.readthedocs.io/en/latest/introduction/getting.html)
  - [Backend configuration](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html)
  - [Talking to your instrument](https://pyvisa.readthedocs.io/en/latest/introduction/communication.html)
  - [A worked, larger example](https://pyvisa.readthedocs.io/en/latest/introduction/example.html)
  - [Reading and writing values](https://pyvisa.readthedocs.io/en/latest/introduction/rvalues.html)
  - [Event handling](https://pyvisa.readthedocs.io/en/latest/introduction/event_handling.html)
  - [Resources](https://pyvisa.readthedocs.io/en/latest/introduction/resources.html)
  - [PyVISA Shell](https://pyvisa.readthedocs.io/en/latest/introduction/shell.html)
  - [VISA resource names](https://pyvisa.readthedocs.io/en/latest/introduction/names.html)

- [Advanced topics](https://pyvisa.readthedocs.io/en/latest/advanced/index.html)
  - [Architecture](https://pyvisa.readthedocs.io/en/latest/advanced/architecture.html)
  - [One frontend driving several backends](https://pyvisa.readthedocs.io/en/latest/advanced/backends.html)
  - [Continuous integration setup](https://pyvisa.readthedocs.io/en/latest/advanced/continuous_integration.html)

- [FAQ](https://pyvisa.readthedocs.io/en/latest/faq/index.html)
  - [Miscellaneous questions](https://pyvisa.readthedocs.io/en/latest/faq/faq.html)
  - [NI-VISA Installation](https://pyvisa.readthedocs.io/en/latest/faq/getting_nivisa.html)
  - [Upgrading from PyVISA < 1.5](https://pyvisa.readthedocs.io/en/latest/faq/migrating.html)

- [API Documentation](https://pyvisa.readthedocs.io/en/latest/api/index.html)
  - [Visa Library](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html)
  - [Resource Manager](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html)
  - [Resource classes](https://pyvisa.readthedocs.io/en/latest/api/resources.html)
  - [Constants module](https://pyvisa.readthedocs.io/en/latest/api/constants.html)
