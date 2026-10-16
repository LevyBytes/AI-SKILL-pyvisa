# An example
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

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

With a `ResourceManager` in hand, call `list_resources` to retrieve available resources. The returned tuple contains [VISA resource names](https://pyvisa.readthedocs.io/en/latest/introduction/names.html#intro-resource-names). That method accepts a dedicated regular-expression syntax for filtering discovered instruments; the details are in [`list_resources()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.list_resources). The default value, `?*::INSTR`, lists only instruments whose resource name ends in '::INSTR', so USB RAW resources and TCPIP SOCKET resources are excluded. To show every present resource, pass `?*` to `list_resources`.

Here, instrument number 14 is a GPIB device, so the `ResourceManager` is asked to open 'GPIB0::14::INSTR' and the returned object is assigned to `my_instrument`.

`open_resource` returns an instance of the `GPIBInstrument` class, which subclasses the more general `Resource`.

```python
>>> print(my_instrument)
<GPIBInstrument('GPIB::14')>

```

Many `Resource` subclasses represent specific resource types, but the `ResourceManager` selects the right class for you. See [Resource classes](https://pyvisa.readthedocs.io/en/latest/api/resources.html#api-resources) for the methods and attributes on each class.

Next, query the device with ``*IDN?``, the standard GPIB message for asking what the instrument is, or sometimes what is currently on its display. `query` abbreviates a `write` that sends the message followed by a `read`.

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

