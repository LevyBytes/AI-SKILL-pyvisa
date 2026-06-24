### Resource Manager

*class *pyvisa.highlevel.ResourceInfo(interface_type, interface_board_number, resource_class, resource_name, alias)

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

*class *pyvisa.highlevel.ResourceManager(visa*library: [str](https://docs.python.org/3/library/stdtypes.html#str) | [VisaLibraryBase](https://pyvisa.readthedocs.io/en/latest/api/visalibrarybase.html#pyvisa.highlevel.VisaLibraryBase) = ''*)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#ResourceManager)

VISA Resource Manager.

close() → [None](https://docs.python.org/3/library/constants.html#None)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#ResourceManager.close)

Close the resource manager session.

Notes

Because resource manager sessions are shared across instances, this also closes connections obtained from other ResourceManager instances.

*property *last_status*: [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)*

Most recent status code returned by an operation using this Resource Manager.

list_resources(query: [str](https://docs.python.org/3/library/stdtypes.html#str) = '?\*::INSTR') → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[[str](https://docs.python.org/3/library/stdtypes.html#str), ...][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#ResourceManager.list_resources)

Return a tuple containing all connected devices that match query.

Notes

The query uses VISA Resource Regular Expression syntax, which differs from Python regular expression syntax. (see below)

VISA Resource Regular Expression syntax is defined by the VISA Library specification: [http://www.ivifoundation.org/docs/vpp43.pdf](http://www.ivifoundation.org/docs/vpp43.pdf)

Symbol Meaning ———- ———-

? Matches exactly one character.

Makes the following character ordinary rather than special.

For example, a question mark after a backslash (?) matches the literal ? character instead of matching any single character.

[list] Matches one character from the enclosed list. You can

use a hyphen to describe a character range.

[^list] Matches any character outside the enclosed list. You can

also use a hyphen to describe a character range.

-

Matches 0 or more repeats of the preceding character or expression.

-

Matches 1 or more repeats of the preceding character or expression.

Exp|exp Matches either the expression before or after the operator. The or

operator | applies to the whole expression before or after it, not only to the adjacent character. For example, VXI|GPIB means (VXI)|(GPIB), not VX(I|G)PIB.

(exp) Groups characters or expressions.

Therefore the default query, '?\*::INSTR', matches any character sequence that ends with '::INSTR'.

On some platforms, resources that are already open are omitted.

list_resources_info(query: [str](https://docs.python.org/3/library/stdtypes.html#str) = '?\*::INSTR') → [Dict](https://docs.python.org/3/library/typing.html#typing.Dict)[[str](https://docs.python.org/3/library/stdtypes.html#str), ResourceInfo][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#ResourceManager.list_resources_info)

Get extended details for all connected devices that match query.

For the VISA Resource Regular Expression syntax used by query, see list_resources().

Returns:

Mapping from resource name to ResourceInfo

Return type:

Dict[[str](https://docs.python.org/3/library/stdtypes.html#str), ResourceInfo]

open_bare_resource(resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str), access_mode: [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes) = AccessModes.no_lock, open_timeout: [int](https://docs.python.org/3/library/functions.html#int) = 0) → [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)[VISASession, [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)][[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#ResourceManager.open_bare_resource)

Open the specified resource without wrapping it in a class.

Parameters:

- **resource_name** ([str](https://docs.python.org/3/library/stdtypes.html#str)) - Resource name or alias to open.

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), \*\*optional) - Access mode for the resource; defaults to constants.AccessModes.no_lock

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) - If the `access_mode` parameter asks for a lock, this absolute wait time (in milliseconds) controls how long the resource may remain locked before an error is returned; defaults to constants.VI_TMO_IMMEDIATE.

Returns:

- VISASession - Unique logical identifier reference for a session.

- StatusCode - Return value from the library call.

  open_resource(resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str), access_mode: [AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes) = AccessModes.no_lock, open_timeout: [int](https://docs.python.org/3/library/functions.html#int) = 0, resource_pyclass: [Type](https://docs.python.org/3/library/typing.html#typing.Type)[[Resource](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource)] | [None](https://docs.python.org/3/library/constants.html#None) = None, \*\*kwargs: [Any](https://docs.python.org/3/library/typing.html#typing.Any)) → [Resource](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource)[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#ResourceManager.open_resource)

Return an instrument matching the resource name.

Parameters:

- **resource_name** ([str](https://docs.python.org/3/library/stdtypes.html#str)) - Resource name or alias to open.

- **access_mode** ([constants.AccessModes](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.AccessModes), \*\*optional) - Access mode for the resource; defaults to constants.AccessModes.no_lock

- **open_timeout** ([int](https://docs.python.org/3/library/functions.html#int), \*\*optional) - If the `access_mode` parameter asks for a lock, this absolute wait time (in milliseconds) controls how long the resource may remain locked before an error is returned; defaults to constants.VI_TMO_IMMEDIATE.

- **resource_pyclass** (Optional**[**Type\*\*[[Resource](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource)]**]**, \*\*optional) - Resource Python class used to instantiate the Resource. Defaults to None, which selects based on the resource name.

- **kwargs** (Any) - Keyword arguments used to modify instrument attributes after construction.

Returns:

Subclass of Resource that matches the resource.

Return type:

[Resource](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource)

resource_info(resource_name: [str](https://docs.python.org/3/library/stdtypes.html#str), extended: [bool](https://docs.python.org/3/library/functions.html#bool) = True) → ResourceInfo[[source]](https://pyvisa.readthedocs.io/en/latest/_modules/pyvisa/highlevel.html#ResourceManager.resource_info)

Get (extended) information for a specific resource.

Parameters:

- **resource_name** ([str](https://docs.python.org/3/library/stdtypes.html#str)) - Unique symbolic name of a resource.

- **extended** ([bool](https://docs.python.org/3/library/functions.html#bool), \*\*optional) - Also retrieve extended information (ie. resource_class, resource_name, alias)

  *property *session*: VISARMSession*

Resource Manager session handle.

Raises:

**errors.InvalidSession** - Raised when the session is closed.
