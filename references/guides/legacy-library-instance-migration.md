# No singleton objects
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

Historical migration guidance for PyVISA 1.5/1.6. Do not treat the old API names as current entrypoints.

### No singleton objects

The first PyVISA design used singleton-style globals: `visa_library` for the library wrapper, as an instance of the old `pyvisa.vpp43.VisaLibrary`, and `resource_manager` for the resource manager, as an instance of the old `pyvisa.visa.ResourceManager`. Importing the package created them. A user could point to another library with `load_library`, but that call did not update `resource_manager`, so the two globals could become inconsistent.

A few other globals also existed, including `status`, which kept the most recent status returned by the library, plus the warning context used to suppress unwanted warnings.

Version 1.5 adds a `VisaLibrary` class and a `ResourceManager` class, both located in `pyvisa.highlevel`. These classes are not strict singletons. Multiple `VisaLibrary` and `ResourceManager` instances are possible, provided they point to different foreign libraries. In code, this means:

```python
>>> lib1 = pyvisa.VisaLibrary("/path/to/my/libvisa.so.7")
>>> lib2 = pyvisa.VisaLibrary("/path/to/my/libvisa.so.7")
>>> lib3 = pyvisa.VisaLibrary("/path/to/my/libvisa.so.8")
>>> lib1 is lib2
True
>>> lib1 is lib3
False

```

Usually you need a `ResourceManager` rather than direct access to a `VisaLibrary` object. You can do:

```python
>>> lib = pyvisa.VisaLibrary("/path/to/my/libvisa.so.7")
>>> rm = lib.resource_manager

```

or equivalently:

```python
>>> rm = pyvisa.ResourceManager("/path/to/my/libvisa.so.7")

```

Note

When no library path is supplied, PyVISA gets it from the user settings file, if that file exists, or otherwise guesses from the OS.

In 1.6, library status is tracked for each resource. Warnings can also be silenced per resource, and `last_status` exposes the stored status.

All together, these changes makes PyVISA thread safe.

