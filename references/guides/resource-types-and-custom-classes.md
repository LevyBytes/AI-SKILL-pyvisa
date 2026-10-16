# Resources
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

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
>>> inst = rm.open_resource('ASRL1::INSTR', resource_pyclass=MessageBasedResource)

```

The sections below cover the `Resource` and `MessageBased` attributes you are most likely to use for Serial, GPIB, and similar resources. See the [API](https://pyvisa.readthedocs.io/en/latest/api/index.html#api) for the complete reference.

