# pyvisa.highlevel.VisaLibraryBase.get_debug_info

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    @staticmethod
    def get_debug_info() -> DebugInfo:
        """Override to return an iterable of lines with the backend debug details."""
        return ["Does not provide debug info"]
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
