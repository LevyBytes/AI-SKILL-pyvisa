# pyvisa.constants.DataWidth.from_literal

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Enclosing source class declaration](data-width-implementation.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
    @classmethod
    def from_literal(cls, value: Literal[8, 16, 32, 64]) -> "DataWidth":
        """Convert a literal width in the proper enum value."""
        if value not in (8, 16, 32, 64):
            raise ValueError(
                f"Invalid datawidth {value} specified. Valid values are (8, 16, 32, 64"
            )
        return cls(value // 8)


# Status code
```

[Source license and checked revision](../../pyvisa-source-license.md).
