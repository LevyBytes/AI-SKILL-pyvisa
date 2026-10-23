# pyvisa.highlevel.ResourceInfo

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Source module scope](../backends/highlevel-module-imports-implementation.md)

```python
#: Resource extended information
#:
#: Named tuple with information about a resource. Returned by some :class:`ResourceManager` methods.
#:
#: :interface_type: Interface type of the given resource string. :class:`pyvisa.constants.InterfaceType`
#: :interface_board_number: Board number of the interface of the given resource string. We allow None
#:                          since serial resources may not sometimes be easily described
#:                          by a single number in particular on Linux system.
#: :resource_class: Specifies the resource class (for example, "INSTR") of the given resource string.
#: :resource_name: This is the expanded version of the given resource string.
#:                 The format should be similar to the VISA-defined canonical resource name.
#: :alias: Specifies the user-defined alias for the given resource string.
ResourceInfo = NamedTuple(
    "ResourceInfo",
    (
        ("interface_type", constants.InterfaceType),
        ("interface_board_number", Optional[int]),
        ("resource_class", Optional[str]),
        ("resource_name", Optional[str]),
        ("alias", Optional[str]),
    ),
)

# Used to properly type the __new__ method
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
