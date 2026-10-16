# Isolated low-level wrapping module
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

Historical migration guidance for PyVISA 1.5/1.6. Do not treat the old API names as current entrypoints.

### Isolated low-level wrapping module

Earlier PyVISA placed the low level implementation (`vpp43`) together with higher level constructs. ctypes handled the wrapping of the VISA library.

In 1.5, that layer became `ctwrapper`. Separating the foreign function calls lets us test them apart from higher level abstractions. It also makes it possible to create new low level modules that high level modules can use as drop in replacements for `ctwrapper`.

In 1.6, `ResourceManager` became the object presented to users. The `VisaLibrary` type can be selected from `library_path` and obtained from a plugin package.

We have two of such packages planned:

- a Mock module for testing a PyVISA program on systems where VISA is not installed.

- a wrapper based on CFFI. CFFI is a new python package for wrapping foreign libraries more easily and more robustly. It may become part of Python in the future.

To support migration, PyVISA 1.5 keeps `vpp43` in the legacy subpackage, reimplemented on top of `ctwrapper`. In 1.6, that module is removed.

Every function formerly available in `vpp43` is now available in `ctwrapper`, with one added first argument: the foreign library wrapper.

The recommended replacement for `vpp43` is to use the `VisaLibrary` object stored on the resource manager's visalib attribute; it exposes all foreign functions as bound methods, as shown below.

