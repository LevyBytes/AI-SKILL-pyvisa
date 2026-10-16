# Architecture
Context: PyVISA advanced; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](backend-development-index.md)

# Architecture, Continuous Integration, Backends

> Pyvisa reference. Original prose; identifiers preserved verbatim.

## Overview

Covers these areas: Architecture; Continuous integration setup; A frontend for multiple backends; Advanced topics.

## Architecture

### Architecture

PyVISA presents its Python-friendly programming interface through three layers:

1. Low-level: the wrapper placed directly around the shared visa library.

This layer declares the argument and return types for every function and handles conversion between Python objects and foreign types.

Direct calls into these functions are rarely needed. When they are necessary, layer 2 probably needs better coverage.

Every level 1 function is exposed as a **static methods** member of [`VisaLibraryBase`](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase).

Warning

Be aware that a backend may omit some low-level functions. For portable code, avoid this layer; the same capabilities should be reachable through the next layer.

Other backends are not required to implement those functions.

2. Middle-level: one Python wrapper function for each function in the shared visa library.

These functions delegate to the low-level calls while adding the extra handling needed for reference-style return values. They also carry complete documentation written for Python users.

Use this layer only when you need to manage a specific VISA library feature that the matching resource class does not expose.

Every level 2 function is available as a **bound methods** member of [`VisaLibraryBase`](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase).

3. High-level: the object-oriented interface built around [`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) and [`Resource`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource).

[`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) provides methods for discovering connected resources. It is also the object used to open resources and create the correct [`Resource`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource) derived class instance.

[`Resource`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource) plus its subclasses give Python-style access to the functions and attributes of the underlying resources.

In ordinary use, creating a [`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) is enough. For a particular resource, call [`open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource) to get the right object. When direct access is required, the `visalib` attribute exposes the `VisaLibrary` object.

`VisaLibrary` performs the low-level calls. With the default IVI Backend, levels 1 and 2 live in the included `pyvisa.ctwrapper` package, whose name means ctypes wrapper.

To select another backend, pass its name to `ResourceManager` after the @ symbol. More detail appears in [A frontend for multiple backends](https://pyvisa.readthedocs.io/en/latest/advanced/backends.html#advanced-backends).

