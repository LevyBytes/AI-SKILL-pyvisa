# pyvisa.resources.PXIInstrument.register
Context: PyVISA pyvisa.resources.PXIInstrument; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](pxi-instrument.md)

```text
classmethod register(interface_type: InterfaceType, resource_class: str) → Callable[[Type[T]], Type[T]]
```

Type and source details:

- [InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)
- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)
- [Type](https://docs.python.org/3/library/typing.html#typing.Type)

Create a decorator to register a class.

The class is associated to an interface type, resource class pair.

Parameters:

- **interface_type** ([constants.InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)) – Interface type for which to register a wrapper class.

- **resource_class** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Resource class for which to register a wrapper class.

Returns:

Class-registration decorator. It raises TypeError when the class being registered lacks required VISA attributes.

Return type:

Callable[[Type[T]], Type[T]]

