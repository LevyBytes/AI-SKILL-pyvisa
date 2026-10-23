# pyvisa.highlevel.VisaLibraryBase.__repr__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def __repr__(self) -> str:
        """str representation of the library including the type of the library."""
        return "<%s(%r)>" % (type(self).__name__, self.library_path)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
