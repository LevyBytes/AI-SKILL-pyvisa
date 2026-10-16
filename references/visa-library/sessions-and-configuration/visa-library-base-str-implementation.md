# pyvisa.highlevel.VisaLibraryBase.__str__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def __str__(self) -> str:
        """str representation of the library."""
        return "Visa Library at %s" % self.library_path
```

[Source license and checked revision](../../pyvisa-source-license.md).
