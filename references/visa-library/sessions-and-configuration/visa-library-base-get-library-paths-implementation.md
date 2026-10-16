# pyvisa.highlevel.VisaLibraryBase.get_library_paths

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    @staticmethod
    def get_library_paths() -> Iterable[LibraryPath]:
        """Override to list the possible library_paths if no path is specified."""
        return ()
```

[Source license and checked revision](../../pyvisa-source-license.md).
