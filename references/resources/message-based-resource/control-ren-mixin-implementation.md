# pyvisa.resources.messagebased.ControlRenMixin

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
class ControlRenMixin(object):
    """Common control_ren method of some messaged based resources."""

    #: Will be present when used as a mixin with Resource
    visalib: VisaLibraryBase

    #: Will be present when used as a mixin with Resource
    session: Any

    # It should work for GPIB, USB and some TCPIP
    # For TCPIP I found some (all?) NI's VISA library do not handle
    # control_ren, but it works for Agilent's VISA library (at least some of
    # them)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
