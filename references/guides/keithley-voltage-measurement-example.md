# A more complex example
Context: PyVISA introduction-3; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](addresses-data-and-backends-index.md)

## A more complex example

### A more complex example

This example demonstrates SCPI command use with a Keithley 2000 multimeter to collect 10 voltage readings. Once the readings are available, the program computes their average and displays it.

The program is described in stages. It begins by initializing the instrument:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager()
>>> keithley = rm.open_resource("GPIB::12")
>>> keithley.write("*rst; status:preset; *cls")

```

At this point, the instrument variable keithley is created for the remaining instrument operations. Right after that, the initialization and reset message is sent to the instrument.

Then the measurement settings are written to the instrument, including the interval time (500ms) and number of readings (10). The details are left to an SCPI and/or Keithley 2000 manual.

```python
>>> interval_in_ms = 500
>>> number_of_readings = 10
>>> keithley.write("status:measurement:enable 512; *sre 1")
>>> keithley.write("sample:count %d" % number_of_readings)
>>> keithley.write("trigger:source bus")
>>> keithley.write("trigger:delay %f" % (interval_in_ms / 1000.0))
>>> keithley.write("trace:points %d" % number_of_readings)
>>> keithley.write("trace:feed sense1; trace:feed:control next")

```

With the instrument configured for measurement, the next three lines wait for a trigger pulse, issue the trigger, and then wait for the instrument to raise a "service request":

```python
>>> keithley.write("initiate")
>>> keithley.assert_trigger()
>>> keithley.wait_for_srq()

```

The service request indicates that measurement is complete and the results can be transferred. Reading them with keithley.query("trace:data?") would work, but the result would be:

```none
-000.0004E+0,-000.0005E+0,-000.0004E+0,-000.0007E+0,
-000.0000E+0,-000.0007E+0,-000.0008E+0,-000.0004E+0,
-000.0002E+0,-000.0005E+0

```

That output would still need conversion into a Python list of numbers. The [`query_ascii_values()`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.query_ascii_values) method handles that conversion:

```python
>>> voltages = keithley.query_ascii_values("trace:data?")
>>> print("Average voltage: ", sum(voltages) / len(voltages))

```

To prepare for another run, reset the instrument's data buffer and SRQ status register. The instrument's manual gives the detailed explanation:

```python
>>> keithley.query("status:measurement?")
>>> keithley.write("trace:clear; trace:feed:control next")

```

Close `keithley` and `rm` when finished; production code should use context managers or `try/finally` for cleanup. SCPI is awkward, but that belongs to a different discussion.
