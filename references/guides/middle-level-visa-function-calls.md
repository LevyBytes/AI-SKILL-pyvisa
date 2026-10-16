# Middle-level
Context: PyVISA advanced; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](backend-development-index.md)

### Middle-level

`VisaLibrary` exposes middle-level functions as bound methods, with a one-to-one mapping from the foreign library.

Each function in the middle layer wraps a single low-level function. For this example:

```text
>>> rm.visalib.map_address(<here goes the arguments>)

```

The wrapper takes care of calling conventions and types.


The angle-bracket text is a signature placeholder. Supply the backend-specific arguments before calling this function.
