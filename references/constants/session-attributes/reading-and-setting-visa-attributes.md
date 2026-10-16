# VISA attributes
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../../guides/installation-and-resource-configuration-index.md)

### VISA attributes

Beyond the attributes already discussed, resources expose most VISA standard attributes through Python properties. Those properties convert between Python values and VISA values, which makes attribute handling easier. Several attributes also provide shorter aliases for convenient access, as shown below:

```python
from pyvisa import constants, ResourceManager
rm = ResourceManager()
instr = rm.open_resource('TCPIP0::1.2.3.4::56789::SOCKET')
instr.io_protocol = constants.VI_PROT_4882_STRS
# is equivalent to
instr.VI_ATTR_IO_PROT = constants.VI_PROT_4882_STRS

```

Note

For the complete set of attributes supported by a resource, inspect [`visa_attributes_classes`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource.visa_attributes_classes). In `pyvisa-shell`, the same kind of information is available with the `attr` command.

VISA attributes can also be read or changed with [`get_visa_attribute`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource.get_visa_attribute) and [`set_visa_attribute`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource.set_visa_attribute). In that lower-level path, you must supply the correct values from [`pyvisa.constants`](https://pyvisa.readthedocs.io/en/latest/api/constants.html#module-pyvisa.constants) both when selecting the attribute and when setting its value.

```python
from pyvisa import constants, ResourceManager
rm = ResourceManager()
instr = rm.open_resource('TCPIP0::1.2.3.4::56789::SOCKET')
instr.set_visa_attribute(constants.VI_ATTR_SUPPRESS_END_EN, constants.VI_TRUE)

```

