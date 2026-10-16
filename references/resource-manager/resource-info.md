# pyvisa.highlevel.ResourceInfo
Context: PyVISA pyvisa.highlevel.ResourceInfo; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../constants/constants-and-resource-manager-index.md) / [Source context](../constants/constants-and-resource-manager-index.md)

### Resource Manager

## Resource Manager
```text
class pyvisa.highlevel.ResourceInfo(
    interface_type,
    interface_board_number,
    resource_class,
    resource_name,
    alias,
)
```

Extended resource information.

Named tuple describing a resource; some `ResourceManager` methods return it.

Interface_type:

Interface type for the given resource string: [`pyvisa.constants.InterfaceType`](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.InterfaceType)

Interface_board_number:

Board number for the interface in the given resource string. None is allowed because serial resources, especially on Linux system, may not always map cleanly to a single number.

Resource_class:

Specifies the resource class, for example "INSTR", for the given resource string.

Resource_name:

Expanded form of the given resource string. Its format should resemble the VISA-defined canonical resource name.

Alias:

User-defined alias specified for the given resource string.

