# pyvisa.resources.GPIBInterface.register
Context: PyVISA pyvisa.resources.GPIBInterface; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resource-class-apis-api-index.md) / [Owning VISA resource class and backend contract](gpib-interface.md)

```text
classmethod register(interface_type: InterfaceType, resource_class: str) → Callable[[Type[T]], Type[T]]
```

Type and source details:

- [InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)
- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [Callable](https://docs.python.org/3/library/typing.html#typing.Callable)
- [Type](https://docs.python.org/3/library/typing.html#typing.Type)

Create a class-registration decorator.

The registered class is tied to an interface type and resource class pair.

Parameters:

- **interface_type** ([constants.InterfaceType](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)) – Interface type for the wrapper class registration.

- **resource_class** ([str](https://docs.python.org/3/library/stdtypes.html#str)) – Resource class for the wrapper class registration.

Returns:

Decorator that registers the class. It raises TypeError when the registered class lacks required VISA attributes.

Return type:

Callable[[Type[T]], Type[T]]

