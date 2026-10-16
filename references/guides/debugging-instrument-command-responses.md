# Making sure the instrument understand the command
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

### Making sure the instrument understand the command

A query exercises both the write path and the read path. Start by separating those halves so you know whether the failure happens while writing or while reading.

For an instrument with a front panel, look there for error messages; some instruments briefly show one right after the read. An error can indicate a malformed command string or a different command set on the instrument, such as legacy commands instead of SCPI commands. If no error appears, either the instrument missed the message terminator or the response cannot be read. Identify which case applies before continuing.

Choose a command that should cause a visible or measurable change, then send it. If no error is reported but the change does not happen, the instrument probably did not recognize the message as complete. That suggests a problem with [`write_termination`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.write_termination). At that point, check the manual again, because some instruments can switch among accepted values, or try standard values such as `\n`, `\r`, a combination of those two, or `\0`.

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

