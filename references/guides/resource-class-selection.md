# Resource class selection
Context: PyVISA PyVISA resources; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../resources/resource-class-apis-api-index.md)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

Resources are high-level objects for working with individual sessions. [`open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource) returns the resource class that matches the requested resource type.

