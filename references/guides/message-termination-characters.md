# Termination characters
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

### Termination characters

The controller needs a way to recognize that an instrument has finished sending a message. The mechanism depends on the bus system. Defaults usually handle termination characters well, but PyVISA lets you adjust them when a device requires different behavior.

A termination setting can be a single character or a multi-character sequence. When that marker appears in the input stream, PyVISA ends the read and returns the accumulated message to the caller. The following read resumes immediately after the termination marker. PyVISA removes the termination characters before delivering the message.

You may set termination characters for each instrument, e.g.

```python
my_instrument.read_termination = '\r'

```

(`\r` is carriage return, usually appearing in the manuals as CR)

Alternatively you can give it when creating your instrument object:

```python
my_instrument = rm.open_resource("GPIB::10", read_termination='\r')

```

The Python resource read-termination setting defaults to `None` in the checked implementation; serial VISA input-end attributes may still use a termination character. Set the values required by the instrument instead of assuming a universal serial terminator.

Set `write_termination` to choose the character appended to outgoing messages.

Note

Internally, PyVISA updates several VISA attributes together so their settings remain consistent. If necessary, you can inspect or modify those attributes directly; see [VISA attributes](../constants/session-attributes/reading-and-setting-visa-attributes.md).

