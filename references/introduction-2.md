# Resources, Getting, Communication

> Pyvisa reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Resources; Installation; Communicating with your instrument.

## Resources

### Resources

In PyVISA, a resource is the object used for an instrument, such as a measurement device. Specialized resource subclasses cover supported categories including GPIB and Serial, and expose the attributes and methods appropriate for the underlying device.

You normally receive these objects from [`open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource) on a [`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) instead of constructing them yourself. At a high level, subclasses of [`Resource`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource) fall into two principal families: [`MessageBasedResource`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource) and [`RegisterBasedResource`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.RegisterBasedResource).

Note

PyVISA chooses the resource Python class from the resource name automatically, but you may override that choice and request a specific Resource Python class:

```python
>>> from pyvisa.resources import MessageBasedResource
>>> inst = rm.open('ASRL1::INSTR', resource_pyclass=MessageBasedResource)

```

The sections below cover the `Resource` and `MessageBased` attributes you are most likely to use for Serial, GPIB, and similar resources. See the [API](https://pyvisa.readthedocs.io/en/latest/api/index.html#api) for the complete reference.

### Attributes of Resource

### session

Every instrument communication channel owns a distinct session handle, and you can retrieve that value:

```python
>>> my_device.session
10442240

```

If the resource is closed, an exception will be raised:

```python
>>> inst.close()
>>> inst.session
Traceback (most recent call last):
...
pyvisa.errors.InvalidSession: Invalid session handle. The resource might be closed.

```

### timeout

Most VISA I/O calls can use a timeout. When configured, any operation that exceeds the timeout stops and raises an exception. Timeout values are stored per instrument in **milliseconds**.

For all PyVISA objects, a timeout is set with

```python
my_device.timeout = 25000

```

In this example, `my_device` can refer to a device, an interface, or a similar target, and the timeout is configured as 25 seconds. For an **infinite** timeout, assign `None`, `float('+inf')`, or:

```python
del my_device.timeout

```

After that, operations on the resource are allowed to run for however long they need, including indefinitely.

For an **immediate** timeout, use 0 or any negative value. In practice, PyVISA treats any value below 1 as immediate.

### Attributes of MessageBase resources

### Chunk length

When data is read from a device, PyVISA needs a buffer before the transfer begins. Because the library has to allocate storage ahead of the read, it must estimate how many bytes the device will provide, and that amount is not known a priori.

PyVISA therefore performs reads in chunks\_. The default chunk size is 20 kilobytes. If unread data remains, PyVISA repeats the read loop, combines the collected pieces, and gives the result back. That 20 kilobytes default is large enough that many transfers finish in a single cycle.

This process is automatic, so it usually requires no attention. Some instruments, however, do not behave well with chunked transfers. If a specific device fails and you expect responses longer than the default chunk length, increase the chunk size, for example with:

```python
my_instrument.chunk_size = 102400

```

This example sets it to 100 kilobytes.

### Termination characters

The controller needs a way to recognize that an instrument has finished sending a message. The mechanism depends on the bus system. Defaults usually handle termination characters well, but PyVISA lets you adjust them when a device requires different behavior.

A termination setting can be a single character or a multi-character sequence. When that marker appears in the input stream, PyVISA ends the read and returns the accumulated message to the caller. The following read resumes immediately after the termination marker. PyVISA removes the termination characters before delivering the message.

You may set termination characters for each instrument, e.g.

```python
my_instrument.read_termination = '\r'

```

(’r’ is carriage return, usually appearing in the manuals as CR)

Alternatively you can give it when creating your instrument object:

```python
my_instrument = rm.open_resource("GPIB::10", read_termination='\r')

```

The bus system determines the default. In most cases the sequence is empty, especially for GPIB; RS232 uses `\r`.

Set `write_termination` to choose the character appended to outgoing messages.

Note

Internally, PyVISA updates several VISA attributes together so their settings remain consistent. If necessary, you can inspect or modify those attributes directly; see the :ref:visa-attr section below.

### query_delay and send_end

There are two further options related to message termination, namely `send_end` and `query_delay`.

`send_end` is a boolean. With the default value, `True`, PyVISA asserts the EOI line after each write to mark completion. EOI is specific to GPIB, although PyVISA applies comparable behavior for other interfaces.

`query_delay` gives the wait time, in seconds, inserted after each write while running a query. For example:

```python
my_instrument = rm.open_resource("GPIB::10", send_end=False, delay=1.2)

```

This configuration uses a 1.2 seconds delay and skips asserting the EOI line. Skipping EOI is not recommended; if you choose that setting anyway, make sure the device protocol calls for it.

### VISA attributes

Beyond the attributes already discussed, resources expose most VISA standard attributes through Python properties. Those properties convert between Python values and VISA values, which makes attribute handling easier. Several attributes also provide shorter aliases for convenient access, as shown below:

```python
from pyvisa import constants, ResourceManager
rm = ResourceManager()
instr = rm.open_resource('TCPIP0::1.2.3.4::56789::SOCKET')
instr.io_protocol = constants.VI_PROT_4882_STRS
# is equivalent to
instr.VI_ATTR_IO_PROT = constants.VI_PROT_4882_STRS

```

Note

For the complete set of attributes supported by a resource, inspect [`visa_attributes_classes`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource.visa_attributes_classes). In `pyvisa-shell`, the same kind of information is available with the `attr` command.

VISA attributes can also be read or changed with [`get_visa_attribute`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource.get_visa_attribute) and [`set_visa_attribute`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource.set_visa_attribute). In that lower-level path, you must supply the correct values from [`pyvisa.constants`](https://pyvisa.readthedocs.io/en/latest/api/constants.html#module-pyvisa.constants) both when selecting the attribute and when setting its value.

```python
from pyvisa import constants, ResourceManager
rm = ResourceManager()
instr = rm.open_resource('TCPIP0::1.2.3.4::56789::SOCKET')
instr.set_visa_attribute(constants.VI_ATTR_SUPPRESS_END_EN, constants.VI_TRUE)

```

## Installation

### Installation

PyVISA serves as a frontend for the VISA library and supports Python 3.6+.

You can install it using [pip](http://www.pip-installer.org/):

```python
$ pip install -U pyvisa

```

### Backend

PyVISA requires a compatible backend before it can communicate with instruments. One bundled backend interfaces with the [National Instruments's VISA](https://www.ni.com/en-us/support/downloads/drivers/download.ni-visa.html) library, but that library must be downloaded and installed separately; see [NI-VISA Installation](https://pyvisa.readthedocs.io/en/latest/faq/getting_nivisa.html#faq-getting-nivisa). VISA libraries are provided by several vendors. PyVISA is tested with [National Instruments's VISA](https://www.ni.com/en-us/support/downloads/drivers/download.ni-visa.html) and [Keysight IO Library Suite](https://www.keysight.com/en/pd-1985909/io-libraries-suite/), both available at no cost, and you only need the driver library rather than a development environment.

Warning

PyVISA supports 32- and 64-bit Python and can use 32- and 64-bit VISA libraries without extra setup. It cannot mix bitness: 64-bit Python cannot load a 32-bit VISA library, and 32-bit Python cannot load a 64-bit VISA library.

**Python and the VISA library must use the same bitness**

Another option is [PyVISA-Py](http://pyvisa-py.readthedocs.io/en/latest/), a pure Python implementation of the VISA standard. Install it with [pip](http://www.pip-installer.org/):

```python
$ pip install -U pyvisa-py

```

Note

PyVISA-Py currently covers only part of the VISA standard, and protocol support varies by bus system. Check its documentation for the details.

### Testing your installation

That is it. To verify that PyVISA installed correctly, start python and create a ResourceManager:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager()
>>> print(rm.list_resources())

```

When a problem comes up, start with the [Miscellaneous questions](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#faq-faq), which collects common fixes and debugging techniques. If those do not resolve it, open an issue in the [issue tracker](https://github.com/pyvisa/pyvisa/issues)

### Using the development version

Install the latest development version directly from [GitHub](https://github.com/pyvisa/pyvisa) if you accept the risk:

```python
$ pip install -U git+https://github.com/pyvisa/pyvisa.git

```

Note

If an older system Python installation should be left alone, try [Anaconda](https://www.anaconda.com/distribution/). It is a free Python distribution from Continuum Analytics with many scientific packages included.

## Communicating with your instrument

### Communicating with your instrument

Note

For users coming from PyVISA releases earlier than 1.5, read [Migrating from PyVISA < 1.5](https://pyvisa.readthedocs.io/en/latest/faq/migrating.html#faq-migrating).

### An example

Start in medias res with a small example:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager()
>>> rm.list_resources()
('ASRL1::INSTR', 'ASRL2::INSTR', 'GPIB0::14::INSTR')
>>> my_instrument = rm.open_resource('GPIB0::14::INSTR')
>>> print(my_instrument.query('*IDN?'))

```

The example demonstrates PyVISA's two main design goals: simple interfaces first, and an object-oriented style.

Import `pyvisa` and create a `ResourceManager`. With no arguments, PyVISA uses the default backend (IVI), which searches for the VISA shared library. If that search fails and pyvisa-py is installed, PyVISA falls back to pyvisa-py. To see the active backend and, when applicable, the shared library path, run:

```python
>>> print(rm)
<ResourceManager('/path/to/visa.so')>

```

Note

PyVISA may fail to find the library and raise an `OSError`. When that happens, find the library path manually and give it to the ResourceManager constructor. Another option is to record the path in a configuration file; see [Configuring the backend](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html#intro-configuring).

With a `ResourceManager` in hand, call `list_resources` to retrieve available resources. The returned tuple contains [VISA resource names](https://pyvisa.readthedocs.io/en/latest/introduction/names.html#intro-resource-names). That method accepts a dedicated regular-expression syntax for filtering discovered instruments; the details are in [`list_resources()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.list_resources). The default value, '?_::INSTR', lists only instruments whose resource name ends in '::INSTR', so USB RAW resources and TCPIP SOCKET resources are excluded. To show every present resource, pass '?_' to `list_resources`.

Here, instrument number 14 is a GPIB device, so the `ResourceManager` is asked to open 'GPIB0::14::INSTR' and the returned object is assigned to my*instrument*.

`open_resource` returns an instance of the `GPIBInstrument` class, which subclasses the more general `Resource`.

```python
>>> print(my_instrument)
<GPIBInstrument('GPIB::14')>

```

Many `Resource` subclasses represent specific resource types, but the `ResourceManager` selects the right class for you. See [Resource classes](https://pyvisa.readthedocs.io/en/latest/api/resources.html#api-resources) for the methods and attributes on each class.

Next, query the device with `'\*IDN?'`, the standard GPIB message for asking what the instrument is, or sometimes what is currently on its display. `query` abbreviates a `write` that sends the message followed by a `read`.

So:

```python
>>> my_instrument.query("*IDN?")

```

is the same as:

```python
>>> my_instrument.write('*IDN?')
>>> print(my_instrument.read())

```

Note

Call `rm.list_opened_resources()` to get every resource that is currently open. It returns a list of `Resource`, but the list is not updated dynamically.

### Getting the instrument configuration right

Most instruments must be configured so they can interpret the computer's message, especially the command terminator, and so the computer can detect when the instrument has finished responding. Without that configuration, you will probably get a `VisaIOError` timeout.

For message based instruments, which cover most use cases, configure the resource's [`read_termination`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.read_termination) and [`write_termination`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.write_termination) attributes. [Resources](https://pyvisa.readthedocs.io/en/latest/introduction/resources.html#intro-resources) describes additional attributes, but this section stays with those two.

Start with the instrument manual when choosing these values. The needed details are usually near the start of the manual's IO operation section. If no value is documented, testing a few standard values is possible, but it is not recommended.

After you have that information, configure the instrument and begin communication like this:

```python
>>> my_instrument.read_termination = '\n'
>>> my_instrument.write_termination = '\n'
>>> my_instrument.query('*IDN?')

```

Here, 'n' is used as the 'line feed'. Another common value is 'r', or 'carriage return'; some instruments use the null byte '0'.

Note

Serial instruments require the correct baud rate. The default baud rate is 9600, but confirm the value for your case in the instrument manual. For other serial settings, [Resource classes](https://pyvisa.readthedocs.io/en/latest/api/resources.html#api-resources) lists the available attributes.

Set a different baud rate for PyVISA communication with your instrument like this:

```python
>>> my_instrument.baud_rate = 57600

```

If everything is configured correctly, the instrument should reply. No reply usually means that at least one setting is wrong, and the manual may not make the required values obvious. The notes below cover common debugging approaches. When they do not solve the problem, you can ask on the PyVISA [issue tracker](https://github.com/pyvisa/pyvisa/issues). Include a detailed description of your setup and the steps you have already tried.

Note

This section does not cover receiving a large ASCII or binary data block; that topic is handled in [Reading and Writing values](https://pyvisa.readthedocs.io/en/latest/introduction/rvalues.html#intro-rvalues).

### Making sure the instrument understand the command

A query exercises both the write path and the read path. Start by separating those halves so you know whether the failure happens while writing or while reading.

For an instrument with a front panel, look there for error messages; some instruments briefly show one right after the read. An error can indicate a malformed command string or a different command set on the instrument, such as legacy commands instead of SCPI commands. If no error appears, either the instrument missed the message terminator or the response cannot be read. Identify which case applies before continuing.

Choose a command that should cause a visible or measurable change, then send it. If no error is reported but the change does not happen, the instrument probably did not recognize the message as complete. That suggests a problem with [`write_termination`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.write_termination). At that point, check the manual again, because some instruments can switch among accepted values, or try standard values such as 'n', 'r', a combination of those two, or '0'.

After you have verified that the command was accepted by the instrument, focus on the read side; it is generally simpler to debug. Try common values for [`read_termination`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.read_termination), and if none helps, use [`read_bytes()`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.read_bytes). That method returns no more than the requested byte count. Reading one byte per attempt can help until a timeout occurs. The byte just before the timeout is probably the termination character. For example:

```python
my_instrument.write('*IDN?')
while True:
    print(my_instrument.read_bytes(1))

```

When [`read_bytes()`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.read_bytes) times out immediately on the first read, the instrument did not send a response. Older instruments may need more time, so wait briefly before reading, for example with time.sleep from the Python standard library. If that does not help, either the command does not produce a response, or the write step is failing; return to the earlier write checks.

Note

A slow instrument may need a longer timeout, or it may require a pause after the write before the read begins. Set that globally with [`query_delay`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.query_delay), or pass `delay=0.1`, for example, to wait 100 ms between writing and reading.

Note

For large data transfers, the elapsed transfer time can be longer than the configured timeout; raising the timeout should resolve that case.

Note

Setting [`read_termination`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.read_termination) to `""` turns off termination-character based detection of an input message's end. Use care with serial instruments: their input-ending behavior is controlled by the `end_input` attribute, and the default uses the termination character. To disable termination characters completely, update `end_input` as well.

Those checks use only PyVISA. On Windows or MacOS, third party tools are often available and can make diagnosis easier. The next section gives tips for using them.

Note

After a communication error, some instruments must be restarted before they communicate correctly again.

### Using third-party softwares

National Instruments and Keysight VISA implementations include diagnostic utilities, such as NIMax and Keysight Connection Expert, for investigating communication setup problems.

Both toolsets can start an interactive session with the instrument and let you adjust settings in a GUI, which is often easier. Follow the same general procedure described earlier. If communication works in one of those tools, PyVISA can usually be configured to work too. If it fails there, PyVISA will fail as well.

For serial instruments, whether native or emulated over USB, you can also communicate directly through Putty or Tera Term on Windows, or through CoolTerm, Terminal / screen on macOS.

These basic checks may be enough to get communication working. If they are not, asking for help is fine, but remember that maintainers usually cannot test against the instrument that is failing in your setup.
