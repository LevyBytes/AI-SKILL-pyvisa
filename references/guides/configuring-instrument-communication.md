# Getting the instrument configuration right
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

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

Here, `\n` is used as the 'line feed'. Another common value is `\r`, or 'carriage return'; some instruments use the null byte `\0`.

Note

Serial instruments require the correct baud rate. The default baud rate is 9600, but confirm the value for your case in the instrument manual. For other serial settings, [Resource classes](https://pyvisa.readthedocs.io/en/latest/api/resources.html#api-resources) lists the available attributes.

Set a different baud rate for PyVISA communication with your instrument like this:

```python
>>> my_instrument.baud_rate = 57600

```

If everything is configured correctly, the instrument should reply. No reply usually means that at least one setting is wrong, and the manual may not make the required values obvious. The notes below cover common debugging approaches. When they do not solve the problem, you can ask on the PyVISA [issue tracker](https://github.com/pyvisa/pyvisa/issues). Include a detailed description of your setup and the steps you have already tried.

Note

This section does not cover receiving a large ASCII or binary data block; that topic is handled in [Reading and Writing values](https://pyvisa.readthedocs.io/en/latest/introduction/rvalues.html#intro-rvalues).

