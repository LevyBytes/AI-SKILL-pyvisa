# pyvisa.highlevel.VisaLibraryBase.get_library_paths

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    @staticmethod
    def get_library_paths() -> Iterable[LibraryPath]:
        """Override to list the possible library_paths if no path is specified."""
        return ()
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
