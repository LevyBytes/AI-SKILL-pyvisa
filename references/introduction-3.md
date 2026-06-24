# Names, Rvalues, Configuring, Example

> Pyvisa reference. Original prose; identifiers preserved verbatim.

## Overview

Coverage includes VISA resource names, reading/writing values, backend setup, and a more complex example.

## VISA resource names

### VISA resource names

To connect through [`open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource), pass the VISA resource name for the desired instrument. In most cases that name begins with the bus type, then the double colon `"::"`, then the instrument's number on that bus. For example,

```none
GPIB::10

```

indicates the GPIB instrument whose number is 10. With two GPIB boards, when the instrument is on board number 1, write

```none
GPIB1::10

```

For the bus portion, valid choices include `"GPIB"`, `"USB"`, and `"ASRL"` (used for a serial/parallel interface). To address an instrument on COM2, use this resource name

```none
ASRL2

```

A serial interface can have only one attached instrument, so no double-colon parameter is included. Still, many VISA implementations accept aliases such as `"COM2"` or `"LPT1"`, and you can define additional aliases yourself.

Resource names ignore case; `"ASRL2"` and `"asrl2"` are equivalent. For deeper details, consult a full VISA reference such as [http://www.ni.com/pdf/manuals/370423a.pdf](http://www.ni.com/pdf/manuals/370423a.pdf).

### VISA Resource Syntax and Examples

(This is adapted from the VISA manual)

The table below gives the address-string grammar. Square brackets ([ ]) mark string segments that are optional.

| Interface         | Syntax                                                                                  |
| ----------------- | --------------------------------------------------------------------------------------- |
| ENET-Serial INSTR | ASRL[0]::host address::serial port::INSTR                                               |
| GPIB INSTR        | GPIB[board]::primary address[::secondary address][::INSTR]                              |
| GPIB INTFC        | GPIB[board]::INTFC                                                                      |
| PXI BACKPLANE     | PXI[interface]::chassis number::BACKPLANE                                               |
| PXI INSTR         | PXI[bus]::device[::function][::INSTR]                                                   |
| PXI INSTR         | PXI[interface]::bus-device[.function][::INSTR]                                          |
| PXI INSTR         | PXI[interface]::CHASSISchassis number::SLOTslot number[::FUNCfunction][::INSTR]         |
| PXI MEMACC        | PXI[interface]::MEMACC                                                                  |
| Remote NI-VISA    | visa://host address[:server port]/remote resource                                       |
| Serial INSTR      | ASRLboard[::INSTR]                                                                      |
| TCPIP INSTR       | TCPIP[board]::host address[::LAN device name][::INSTR]                                  |
| TCPIP SOCKET      | TCPIP[board]::host address::port::SOCKET                                                |
| USB INSTR         | USB[board]::manufacturer ID::model code::serial number[::USB interface number][::INSTR] |
| USB RAW           | USB[board]::manufacturer ID::model code::serial number[::USB interface number]::RAW     |
| VXI BACKPLANE     | VXI[board][::VXI logical address]::BACKPLANE                                            |
| VXI INSTR         | VXI[board]::VXI logical address[::INSTR]                                                |
| VXI MEMACC        | VXI[board]::MEMACC                                                                      |
| VXI SERVANT       | VXI[board]::SERVANT                                                                     |

Choose GPIB for communication with GPIB resources. Choose VXI for VXI resources reached through embedded, MXIbus, or 1394 controllers. Choose ASRL for an asynchronous serial device such as RS-232 or RS-485. Choose PXI for PXI and PCI resources. Choose TCPIP when the transport is Ethernet.

The following table shows the default value for optional string segments.

| Optional String Segments | Default Value                      |
| ------------------------ | ---------------------------------- |
| board                    | 0                                  |
| GPIB secondary address   | none                               |
| LAN device name          | inst0                              |
| PXI bus                  | 0                                  |
| PXI function             | 0                                  |
| USB interface number     | lowest numbered relevant interface |

The following table shows examples of address strings:

| Address String                   | Description                                                                                                                                                                                    |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ASRL::1.2.3.4::2::INSTR          | Serial device on port 2 for the ENET Serial controller at address 1.2.3.4.                                                                                                                     |
| ASRL1::INSTR                     | A serial device attached to interface ASRL1.                                                                                                                                                   |
| GPIB::1::0::INSTR                | GPIB device on GPIB interface 0 with primary address 1 and secondary address 0.                                                                                                                |
| GPIB2::INTFC                     | Interface or raw board resource for GPIB interface 2.                                                                                                                                          |
| PXI::15::INSTR                   | PXI device number 15 on bus 0 with implied function 0.                                                                                                                                         |
| PXI::2::BACKPLANE                | Backplane resource for chassis 2 in the default PXI system, where the interface is 0.                                                                                                          |
| PXI::CHASSIS1::SLOT3             | PXI device in slot number 3 in the PXI chassis configured as chassis 1.                                                                                                                        |
| PXI0::2-12.1::INSTR              | PXI bus number 2, device 12 with function 1.                                                                                                                                                   |
| PXI0::MEMACC                     | PXI MEMACC session.                                                                                                                                                                            |
| TCPIP::dev.company.com::INSTR    | TCP/IP device at the given address, accessed through VXI-11 or LXI. It assumes the default LAN Device Name, inst0.                                                                             |
| TCPIP0::1.2.3.4::999::SOCKET     | Raw TCP/IP access to port 999 at the specified IP address.                                                                                                                                     |
| USB::0x1234::125::A22-5::INSTR   | USB Test & Measurement class device identified by manufacturer ID 0x1234, model code 125, and serial number A22-5. It selects the device's first available USBTMC interface, usually number 0. |
| USB::0x5678::0x33::SN999::1::RAW | Raw USB nonclass device identified by manufacturer ID 0x5678, model code 0x33, and serial number SN999. It selects interface number 1 on the device.                                           |
| visa://hostname/ASRL1::INSTR     | The resource ASRL1::INSTR on the specified remote system.                                                                                                                                      |
| VXI::1::BACKPLANE                | Mainframe resource for chassis 1 in the default VXI system, where the interface is 0.                                                                                                          |
| VXI::MEMACC                      | Board-level register access to the VXI interface.                                                                                                                                              |
| VXI0::1::INSTR                   | A VXI device at logical address 1 in VXI interface VXI0.                                                                                                                                       |
| VXI0::SERVANT                    | Servant/device-side resource for VXI interface 0.                                                                                                                                              |

## Reading and Writing values

### Reading and Writing values

Some instruments can exchange large datasets with the computer using one query. For instance, an oscilloscope may return an entire voltage trace, while an arbitrary wave generator may require you to send the function it should generate.

These transfers usually use either ASCII form, which is slower but easy to read, or binary form, which is faster but harder to inspect during debugging.

PyVISA Message Based Resources have different methods for this called [`read_ascii_values()`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.read_ascii_values), [`query_ascii_values()`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.query_ascii_values) and [`read_binary_values()`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.read_binary_values), [`query_binary_values()`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.MessageBasedResource.query_binary_values).

### Reading ASCII values

Suppose your oscilloscope, opened as `inst`, is set to return **ASCII** data for the `CURV?` command. Then you can query the values with:

```python
>>> values = inst.query_ascii_values('CURV?')

```

`values` will be `list` containing the values from the device.

Often a `list` is not the desired result; you may prefer another container type, for example a `numpy.array`. One option is to convert the returned data afterward:

```python
>>> values = np.array(inst.query_ascii_values('CURV?'))

```

At times, avoiding that temporary list is more efficient. In those cases, pass the wanted container type directly with the query:

```python
>>> values = inst.query_ascii_values('CURV?', container=numpy.array)

```

In `container`, you can have any callable/type that takes an iterable.

Note

For numpy.array or numpy.ndarray containers, PyVISA can call numpy routines and avoid an intermediate representation during conversion.

Some devices send ASCII data as hex or oct instead of decimal numbers, and others may return an array of strings. For those cases, provide a `converter`. For example, when the expected integers are hex:

```python
>>> values = inst.query_ascii_values('CURV?', converter='x')

```

`converter` may be one of the Python [string formatting codes](https://docs.python.org/3/library/string.html#formatspec), or a callable that accepts one argument when you need custom behavior. The default converter is `'f'`.

Finally, some devices separate returned values with an unusual delimiter. If, for example, the separator is `'$'`, make this call:

```python
>>> values = inst.query_ascii_values('CURV?', separator='$')

```

You may supply a function that receives a string and returns an iterable. The separator defaults to `','` (comma).

### Reading binary values

When the oscilloscope stored in `inst` is set to send data as **BINARY** for `CURV?`, identify the datatype in use, such as uint8, int8, single, double, etc. PyVISA follows the naming convention used by the [struct module](https://docs.python.org/3/library/struct.html#format-characters).

The endianness is another required detail. PyVISA defaults to little-endian. For doubles d in big endian, use this call:

```python
>>> values = inst.query_binary_values('CURV?', datatype='d', is_big_endian=True)

```

The output container type can be set too, following the earlier pattern.

PyVISA treats data blocks as following the IEEE convention by default. For an HP data block, pass `header_fmt='hp'` to `read_binary_values`. For data sent without a header, use `header_fmt='empty'`.

By default PyVISA expects a termination character after the data block and reads it to prevent parsing problems. That works for many devices, but instruments that omit the termination character can cause a timeout. If that happens, first confirm that the instrument is readable by checking the response with `read_raw` (possibly more than once). Then compare the advertized length of the block with the bytes returned by the instrument, plus the header. When those values agree, pass `expect_termination=False`; PyVISA will stop waiting for a final termination character.

You may pass an optional monitoring interface object, for example a tqdm progress bar, to the read_binary_values() and query_binary_values() methods. It helps when an application downloads large records from instruments such as oscilloscopes. Each method updates the monitoring object with the byte count read from the instrument. When that object is a progress bar, initialize it with the total number of bytes expected from the instrument. The object must provide an update() method. See the tqdm package documentation for details.

To include header and termination bytes in a transfer-size calculation, use pyvisa.util.message_length.

An implementation of a progress bar might look like:

```python
from pyvisa import resource_manager
from pyvisa.util import message_length

inst = resource_manager.open_resource(...)

# calculate the total number of bytes to download
total_bytes = message_length(num_points=1000, datatype="f", header_format="ieee")

# create a download monitor and use it when downloading data
with tqdm(desc="Downloading", unit="B", total=total_bytes) as progress_bar:
    inst.write("CURV?")
    data = inst.read_binary_values(monitoring_interface=progress_bar)

```

If reads from the instrument work normally but this method cannot fetch the entire message (VI_ERROR_CONN_LOST, VI_ERROR_INV_SETUP, or Python simply crashes), experiment with `chunk_size` values; the default is 20\*1024. The cause is not well understood, but changing `chunk_size` is a known workaround. Larger chunks can also speed up large transfers.

Some instruments use protocols that do not report the byte count in advance. For example, the Keithley 2000 always sends the complete buffer, with its size reported by `trace:points?`. Because a binary block can include the termination character, PyVISA must know the expected byte count. In those cases, provide the point count with `data_points`; PyVISA infers the bytes from the block datatype.

When reading something like a file and you only need a bytes object, use the `"s"` datatype with `bytes` as the container.

### Writing ASCII values

For an arbitrary wave generator, uploading a function shape might use `WLISt:WAVeform:DATA <waveform name>,<function data>`; `<waveform name>` is the storage name on the device.

```python
>>> values = list(range(100))
>>> inst.write_ascii_values('WLISt:WAVeform:DATA somename,', values)

```

Again, you can specify the converter code.

```python
>>> inst.write_ascii_values('WLISt:WAVeform:DATA somename,', values, converter='x')

```

`converter` accepts any Python [string formatting codes](https://docs.python.org/3/library/string.html#formatspec), or, when necessary, a callable that receives one argument. Its default value is `'f'`.

The separator can also be specified just like in `query_ascii_values`.

```python
>>> inst.write_ascii_values('WLISt:WAVeform:DATA somename,', values, converter='x', separator='$')

```

You may supply a function that receives an iterable and returns a string. The separator defaults to `','` (comma).

### Writing binary values

A binary upload of a function shape to an arbitrary wave generator can use a command such as `WLISt:WAVeform:DATA <waveform name>,<function data>`; the device stores the data under `<waveform name>`.

```python
>>> values = list(range(100))
>>> inst.write_binary_values('WLISt:WAVeform:DATA somename,', values)

```

Again you can specify the `datatype` and `endianness`.

```python
>>> inst.write_binary_values('WLISt:WAVeform:DATA somename,', values, datatype='d', is_big_endian=False)

```

For data already stored in a `bytes` object, use the `"s"` format.

### When things are not what they should be

PyVISA makes transfers to and from a device straightforward. The methods above handle 99% of situations, but a device can still ignore standard protocols so completely that none of the arguments described earlier can adapt to it.

In those cases, you need to get the data:

```python
>>> inst.write('CURV?')
>>> data = inst.read_raw()

```

and then you need to implement the logic to parse it.

If the read_raw call fails instead, try reading only a small number of bytes with:

```python
>>> inst.write('CURV?')
>>> data = inst.read_bytes(1)

```

A failure here can mean the instrument did not respond because it needs additional time, or because the first instruction was not understood.

## Configuring the backend

### Configuring the backend

At present, two backends are available: the pyvisa backend that uses an IVI library (including NI-VISA, Keysight VISA, R&S VISA, tekVISA, etc.), and pyvisa-py, a pure python implementation of the VISA library. Without an explicit backend, pyvisa chooses the IVI backend when an IVI library is installed (details are in the next section); otherwise it falls back to pyvisa-py.

A backend can also be chosen by passing a parameter to ResourceManager; this example selects pyvisa-py:

```python
>>> pyvisa.ResourceManager('@py')

```

Another option is setting the PYVISA_LIBRARY environment variable, which accepts the same values as the ResourceManager constructor.

### Configuring the IVI backend

Note

The IVI backend requires an IVI-VISA library to be installed first. NI-VISA is one option, but another IVI-VISA library can be used. For NI-VISA details, see ([NI-VISA Installation](https://pyvisa.readthedocs.io/en/latest/faq/getting_nivisa.html#faq-getting-nivisa)).

PyVISA usually locates the shared visa library without extra configuration. When autodetection fails, or when a different library should be selected, pass the library path to the [`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) constructor:

```python
>>> rm = ResourceManager('Path to library')

```

To make this library the default for every PyVISA application, put the setting in a `.pyvisarc` file (including the leading dot) in your [home directory](http://en.wikipedia.org/wiki/Home_directory).

| Operating System          | Location                                   |
| ------------------------- | ------------------------------------------ |
| Windows NT                | `<root>\WINNT\Profiles\<username>`         |
| Windows 2000, XP and 2003 | `<root>\Documents and Settings\<username>` |
| Windows Vista, 7 or 8     | `<root>\Users\<username>`                  |
| Mac OS X                  | `/Users/<username>`                        |
| Linux                     | `/home/<username>` (depends on the distro) |

On Windows XP, for instance, place the file in the "Documents and Settings" user folder; if your login account is "smith", the path would be `C:\Documents and Settings\smith\.pyvisarc`.

The file uses INI syntax. For instance, when the library resides at `/usr/lib/libvisa.so.7`, `.pyvisarc` should include this content:

```python
[Paths]

VISA library: /usr/lib/libvisa.so.7

```

Please note that [Paths] is treated case-sensitively.

On Windows, additional .dll lookup directories can be supplied with a .pyvisarc file using this pattern:

```python
[Paths]

dll_extra_paths: C:\Program Files\Keysight\IO Libraries Suite\bin;C:\Program Files (x86)\Keysight\IO Libraries Suite\bin

```

A site-wide configuration file may be placed at `/usr/share/pyvisa/.pyvisarc` (`/usr/local/...` is another possibility, depending on where Python is installed). On Windows, the usual location is `c:\Python37\share\pyvisa\.pyvisarc`.

When a problem comes up, consult the [Frequently asked questions](https://pyvisa.readthedocs.io/en/latest/faq/index.html#faq). That page covers common fixes and practical debugging techniques. If nothing resolves the issue, open a report in the [issue tracker](https://github.com/pyvisa/pyvisa/issues)

## A more complex example

### A more complex example

This example demonstrates SCPI command use with a Keithley 2000 multimeter to collect 10 voltage readings. Once the readings are available, the program computes their average and displays it.

The program is described in stages. It begins by initializing the instrument:

```python
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

That is the whole sequence: 18 lines of clear code. SCPI is awkward, but that belongs to a different discussion.
