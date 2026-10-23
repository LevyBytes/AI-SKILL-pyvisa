# pyvisa.highlevel.get_wrapper_class

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](highlevel-implementation-index.md)

```python
def get_wrapper_class(backend_name: str) -> Type[VisaLibraryBase]:
    """Return the WRAPPER_CLASS for a given backend."""
    try:
        return _WRAPPERS[backend_name]
    except KeyError:
        if backend_name == "ivi":
            from .ctwrapper import IVIVisaLibrary

            _WRAPPERS["ivi"] = IVIVisaLibrary
            return IVIVisaLibrary

    pkg: PyVISAModule
    try:
        pkg = cast(PyVISAModule, import_module("pyvisa_" + backend_name))
        _WRAPPERS[backend_name] = cls = pkg.WRAPPER_CLASS
        return cls
    except ImportError:
        raise ValueError("Wrapper not found: No package named pyvisa_%s" % backend_name)

def _get_default_wrapper() -> str:
    """Return an available default VISA wrapper as a string ('ivi' or 'py').

    Prefer IVI when its binary is present; otherwise check pyvisa-py.

    'ni' VISA wrapper is NOT used since version > 1.10.0
    and will be removed in 1.12

    Raises
    ------
    ValueError
        If no backend can be found

    """

    from .ctwrapper import IVIVisaLibrary

    ivi_binary_found = bool(IVIVisaLibrary.get_library_paths())
    if ivi_binary_found:
        logger.debug("The IVI implementation available")
        return "ivi"
    else:
        logger.debug("Did not find IVI binary")

    try:
        get_wrapper_class("py")  # check for pyvisa-py availability
        logger.debug("pyvisa-py is available.")
        return "py"
    except ValueError:
        logger.debug("Did not find pyvisa-py package")
    raise ValueError(
        "No VISA implementation was found. Install the IVI binary or pyvisa-py."
    )
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
