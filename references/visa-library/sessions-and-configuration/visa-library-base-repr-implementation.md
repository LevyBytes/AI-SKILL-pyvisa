# pyvisa.highlevel.VisaLibraryBase.__repr__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def __repr__(self) -> str:
        """str representation of the library including the type of the library."""
        return "<%s(%r)>" % (type(self).__name__, self.library_path)
```

[Source license and checked revision](../../pyvisa-source-license.md).
