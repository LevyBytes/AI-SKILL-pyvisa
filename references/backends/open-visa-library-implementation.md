# pyvisa.highlevel.open_visa_library

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](highlevel-implementation-index.md)

```python
def open_visa_library(specification: str = "") -> VisaLibraryBase:
    """Helper function to create a VISA library wrapper.

    In general, you should not use the function directly. The VISA library
    wrapper will be created automatically when you create a ResourceManager object.

    Parameters
    ----------
    specification : str, optional
        The specification contains 2 parts split at '@', ex: path/visa.dll@ivi
        The second part names the backend (ivi, py, ...), while the first part
        is passed to the library object. For the ivi backend it should be the
        path to the VISA library.
        Either part may be omitted. When the second part is absent, the system
        uses the ivi backend if available, or the pyvisa-py backend if the
        first part is also omitted.

    """

    if not specification:
        logger.debug("No visa library specified, trying to find alternatives.")
        try:
            specification = os.environ["PYVISA_LIBRARY"]
        except KeyError:
            logger.debug("Environment variable PYVISA_LIBRARY is unset.")

    wrapper: Optional[str]
    try:
        argument, wrapper = specification.rsplit("@", 1)
    except ValueError:
        argument = specification
        wrapper = None  # Flag that we need a fallback, but avoid nested exceptions
    if wrapper is None:
        if argument:  # some filename given
            wrapper = "ivi"
        else:
            wrapper = _get_default_wrapper()

    cls = get_wrapper_class(wrapper)

    try:
        return cls(argument)
    except Exception as e:
        logger.debug("Unable to open VISA wrapper %s using %s\n%s", cls, str(argument), e)
        raise
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
