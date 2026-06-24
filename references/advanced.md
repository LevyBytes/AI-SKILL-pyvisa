# Architecture, Continuous Integration, Backends

> Pyvisa reference. Original prose; identifiers preserved verbatim.

## Overview

Covers these areas: Architecture; Continuous integration setup; A frontend for multiple backends; Advanced topics.

## Architecture

### Architecture

PyVISA presents its Python-friendly programming interface through three layers:

>

1.

Low-level: the wrapper placed directly around the shared visa library.

This layer declares the argument and return types for every function and handles conversion between Python objects and foreign types.

Direct calls into these functions are rarely needed. When they are necessary, layer 2 probably needs better coverage.

Every level 1 function is exposed as a **static methods** member of [`VisaLibraryBase`](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase).

Warning

Be aware that a backend may omit some low-level functions. For portable code, avoid this layer; the same capabilities should be reachable through the next layer.

Other backends are not required to implement those functions.

2.

Middle-level: one Python wrapper function for each function in the shared visa library.

These functions delegate to the low-level calls while adding the extra handling needed for reference-style return values. They also carry complete documentation written for Python users.

Use this layer only when you need to manage a specific VISA library feature that the matching resource class does not expose.

Every level 2 function is available as a **bound methods** member of [`VisaLibraryBase`](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase).

3.

High-level: the object-oriented interface built around [`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) and [`Resource`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource).

[`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) provides methods for discovering connected resources. It is also the object used to open resources and create the correct [`Resource`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource) derived class instance.

[`Resource`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource) plus its subclasses give Python-style access to the functions and attributes of the underlying resources.

In ordinary use, creating a [`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) is enough. For a particular resource, call [`open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource) to get the right object. When direct access is required, the `visalib` attribute exposes the `VisaLibrary` object.

`VisaLibrary` performs the low-level calls. With the default IVI Backend, levels 1 and 2 live in the included `pyvisa.ctwrapper` package, whose name means ctypes wrapper.

To select another backend, pass its name to `ResourceManager` after the @ symbol. More detail appears in [A frontend for multiple backends](https://pyvisa.readthedocs.io/en/latest/advanced/backends.html#advanced-backends).

### Calling middle- and low-level functions

After creating a [`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager):

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager()

```

the related `VisaLibrary` instance is available through the `visalib` attribute.

For example, the VISA function `viMapAddress` is exposed in the low-level layer as the static method `viMapAddress` on the `visalib` attributed and in the middle-level layer as `map_address`.

The function names indicate which layer they belong to. Low-level functions keep the shared-library name and use the **vi** prefix. Middle-level functions use names that are more Pythonic but still recognizable: the leading **vi** is usually removed from camelCase names, then the remainder is converted to lowercase words separated by underscores. Documentation for these methods is in [API](https://pyvisa.readthedocs.io/en/latest/api/index.html#api).

### Low-level

Low-level functions are directly available as static methods, for example:

```python
>>> rm.visalib.viMapAddress(<here goes the arguments>)

```

Calling these functions requires knowing the declaration and the Python interface details. For a more convenient route, the `VisaLibrary` object also supplies middle-level functions.

When using these methods, you will probably also need the VISA constants. Those constants are documented in [Constants module](https://pyvisa.readthedocs.io/en/latest/api/constants.html#api-constants)

### Middle-level

`VisaLibrary` exposes middle-level functions as bound methods, with a one-to-one mapping from the foreign library.

Each function in the middle layer wraps a single low-level function. For this example:

```python
>>> rm.visalib.map_address(<here goes the arguments>)

```

The wrapper takes care of calling conventions and types.

## Continuous integration setup

### Continuous integration setup

Comprehensive PyVISA testing is difficult because it needs both a VISA library implementation and real instruments. Without those pieces, coverage mostly reaches utility code and infrastructure. Those limited tests live at the root of the pyvisa testsuite package and run on every commit through Github Actions together with linters and documentation builds.

Keysight tools made available to PyVISA developers allow most message based resource capabilities to be tested as well. Because the build bots need hardware, those tests cannot run on typical hosted CIs services such as Travis, Azure, Github actions, etc.

A self-hosted builder can execute tests that depend on those tools. PyVISA developer selected Azure Pipelines for self-hosted runners because Azure is simple to use and should keep builder maintenance low while Azure handles the CI service itself. Github Actions was considered too, but for security reason self-hosted runners should not execute on forks, and Github Actions currently offers no way to block self-hosted runners from forked runs.

An Azure self-hosted runner is in place and stays active till December 2020. It can test only TCPIP based resources. A replacement runner is planned for the first trimester of 2021, hopefully adding USB::INSTR and GPIB resource support.

The current runner setup is imperfect, so it may occasionally go offline. If this happen before December 2020, contact @MatthieuDartiailh on Github.

Note

The current runner uses Windows and conda. Because of how Windows activation scripts work, calls to activate or conda activate have to be preceded by call.

## A frontend for multiple backends

### A frontend for multiple backends

A short history helps explain this section. PyVISA began as a Python wrapper for the VISA library, more precisely a [`ctypes`](https://docs.python.org/3/library/ctypes.html#module-ctypes) wrapper around NI-VISA. That design worked, but it made alternative instrument communication paths hard to develop on platforms without NI-VISA. Users also had to change programs when switching to packages with different API.

Since 1.6, PyVISA has acted as a frontend to VISA. It offers a Pythonic API that can connect to several backends. Each backend provides a class derived from VisaLibraryBase to implement low-level communication. The default backend, called **ivi**, is the bundled ctypes wrapper around IVI-VISA. In practice, IVI-VISA may be NI-VISA, Keysight VISA, R&S VISA, tekVISA etc. By default, PyVISA calls whichever library is installed on the system as the VISA library.

Select the backend at resource manager creation time with the `@` symbol. Since **ivi** is the default, this:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager()

```

is equivalent to this:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager('@ivi')

```

If needed, you can still include the library path:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager('/path/to/lib@ivi')

```

Internally, [`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) locates the requested backend and instantiates the VISA library it supplies.

PyVISA resolves backends by name. With:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager('@somename')

```

PyVISA attempts to import an installed package/module named `pyvisa_somename` from your system. This keeps backend discovery loosely coupled and configuration free, because PyVISA only learns about a backend when you try to use it.

Run this command line code to list installed backends:

```python
pyvisa-info

```

### Developing a new Backend

A minimum backend is quite small:

```python
from pyvisa.highlevel import VisaLibraryBase

class MyLibrary(VisaLibraryBase):
    pass

WRAPPER_CLASS = MyLibrary

```

You may also provide a staticmethod named get_debug_info that returns a dictionary of debug information printed by `pyvisa-info`

When developing a backend, one key decision is which VisaLibraryBase methods to implement and which API to expose.

A **complete** VISA Library implementation needs many functions, essentially nearly every level 2 function described in [Architecture](https://pyvisa.readthedocs.io/en/latest/advanced/architecture.html#advanced-architecture), with a full list at the end of this page. A usable implementation, however, does not have to provide all of them.

The **very minimum** set is:

>

- **open_default_resource_manager**: returns a session for the Default Resource Manager resource.

- **open**: Starts a session for the specified resource.

- **close**: Ends the specified session, event, or find list.

- **list_resources**: Returns a tuple containing every connected device that matches query.

(the signature is available below and in [Visa Library](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#api-visalibrarybase))

Note

[`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) checks for a `pyvisa.highlevel.VisaLibraryBase.open_resource` attribute so a new backend implementation can provide custom opening behavior.

That minimal set is not enough for much useful work. Commonly, you also need:

>

- **get_attribute**: Gets the current state of an attribute.

- **set_atribute**: Updates the state of an attribute.

To send bytes to MessageBased instruments, add:

>

- **read**: Synchronously reads data from a device or interface.

- **write**: Synchronously writes data to a device or interface.

Other devices or use cases may require additional functions; the exact set depends on your needs.

When appropriate, these functions should raise `pyvisa.errors.VisaIOError` or emit `pyvisa.errors.VisaIOWarning`, and they should store the error code per session. The simple way to do that is to call [`handle_return_value()`](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase.handle_return_value) with the session and return value.

Complete level 2 function list for implementation:

```python
def read_memory(self, session, space, offset, width, extended=False):
def write_memory(self, session, space, offset, data, width, extended=False):
def move_in(self, session, space, offset, length, width, extended=False):
def move_out(self, session, space, offset, length, data, width, extended=False):
def peek(self, session, address, width):
def poke(self, session, address, width, data):
def assert_interrupt_signal(self, session, mode, status_id):
def assert_trigger(self, session, protocol):
def assert_utility_signal(self, session, line):
def buffer_read(self, session, count):
def buffer_write(self, session, data):
def clear(self, session):
def close(self, session):
def disable_event(self, session, event_type, mechanism):
def discard_events(self, session, event_type, mechanism):
def enable_event(self, session, event_type, mechanism, context=None):
def flush(self, session, mask):
def get_attribute(self, session, attribute):
def gpib_command(self, session, data):
def gpib_control_atn(self, session, mode):
def gpib_control_ren(self, session, mode):
def gpib_pass_control(self, session, primary_address, secondary_address):
def gpib_send_ifc(self, session):
def in_8(self, session, space, offset, extended=False):
def in_16(self, session, space, offset, extended=False):
def in_32(self, session, space, offset, extended=False):
def in_64(self, session, space, offset, extended=False):
def install_handler(self, session, event_type, handler, user_handle):
def list_resources(self, session, query='?*::INSTR'):
def lock(self, session, lock_type, timeout, requested_key=None):
def map_address(self, session, map_space, map_base, map_size,
def map_trigger(self, session, trigger_source, trigger_destination, mode):
def memory_allocation(self, session, size, extended=False):
def memory_free(self, session, offset, extended=False):
def move(self, session, source_space, source_offset, source_width, destination_space,
def move_asynchronously(self, session, source_space, source_offset, source_width,
def move_in_8(self, session, space, offset, length, extended=False):
def move_in_16(self, session, space, offset, length, extended=False):
def move_in_32(self, session, space, offset, length, extended=False):
def move_in_64(self, session, space, offset, length, extended=False):
def move_out_8(self, session, space, offset, length, data, extended=False):
def move_out_16(self, session, space, offset, length, data, extended=False):
def move_out_32(self, session, space, offset, length, data, extended=False):
def move_out_64(self, session, space, offset, length, data, extended=False):
def open(self, session, resource_name,
def open_default_resource_manager(self):
def out_8(self, session, space, offset, data, extended=False):
def out_16(self, session, space, offset, data, extended=False):
def out_32(self, session, space, offset, data, extended=False):
def out_64(self, session, space, offset, data, extended=False):
def parse_resource(self, session, resource_name):
def parse_resource_extended(self, session, resource_name):
def peek_8(self, session, address):
def peek_16(self, session, address):
def peek_32(self, session, address):
def peek_64(self, session, address):
def poke_8(self, session, address, data):
def poke_16(self, session, address, data):
def poke_32(self, session, address, data):
def poke_64(self, session, address, data):
def read(self, session, count):
def read_asynchronously(self, session, count):
def read_stb(self, session):
def read_to_file(self, session, filename, count):
def set_attribute(self, session, attribute, attribute_state):
def set_buffer(self, session, mask, size):
def status_description(self, session, status):
def terminate(self, session, degree, job_id):
def uninstall_handler(self, session, event_type, handler, user_handle=None):
def unlock(self, session):
def unmap_address(self, session):
def unmap_trigger(self, session, trigger_source, trigger_destination):
def usb_control_in(self, session, request_type_bitmap_field, request_id, request_value,
def usb_control_out(self, session, request_type_bitmap_field, request_id, request_value,
def vxi_command_query(self, session, mode, command):
def wait_on_event(self, session, in_event_type, timeout):
def write(self, session, data):
def write_asynchronously(self, session, data):
def write_from_file(self, session, filename, count):

```

## Advanced topics

### Advanced topics

This section covers PyVISA internals, especially the details of how PyVISA manages backends.

- [Architecture](https://pyvisa.readthedocs.io/en/latest/advanced/architecture.html)
  - [Calling middle- and low-level functions](https://pyvisa.readthedocs.io/en/latest/advanced/architecture.html#calling-middle-and-low-level-functions)

- [A frontend for multiple backends](https://pyvisa.readthedocs.io/en/latest/advanced/backends.html)
  - [Developing a new Backend](https://pyvisa.readthedocs.io/en/latest/advanced/backends.html#developing-a-new-backend)

- [Continuous integration setup](https://pyvisa.readthedocs.io/en/latest/advanced/continuous_integration.html)
