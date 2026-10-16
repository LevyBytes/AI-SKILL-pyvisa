# Reading binary values
Context: PyVISA introduction-3; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](addresses-data-and-backends-index.md)

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
import pyvisa
from pyvisa.util import message_length
from tqdm import tqdm

# Select a real resource and configure its binary format and terminator first.
resource_name = "TCPIP::192.168.0.2::INSTR"
with pyvisa.ResourceManager() as rm, rm.open_resource(resource_name) as inst:
    total_bytes = message_length(num_points=1000, datatype="f", header_format="ieee")
    with tqdm(desc="Downloading", unit="B", total=total_bytes) as progress_bar:
        inst.write("CURV?")
        data = inst.read_binary_values(datatype="f", monitoring_interface=progress_bar)
```

If reads from the instrument work normally but this method cannot fetch the entire message (VI_ERROR_CONN_LOST, VI_ERROR_INV_SETUP, or Python simply crashes), experiment with `chunk_size` values; the default is 20\*1024. The cause is not well understood, but changing `chunk_size` is a known workaround. Larger chunks can also speed up large transfers.

Some instruments use protocols that do not report the byte count in advance. For example, the Keithley 2000 always sends the complete buffer, with its size reported by `trace:points?`. Because a binary block can include the termination character, PyVISA must know the expected byte count. In those cases, provide the point count with `data_points`; PyVISA infers the bytes from the block datatype.

When reading something like a file and you only need a bytes object, use the `"s"` datatype with `bytes` as the container.

