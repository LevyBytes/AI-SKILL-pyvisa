# PyVisa Info
Context: PyVISA introduction; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](events-and-visa-shell-index.md)

### PyVisa Info

You can invoke it from the command-line:

```console
pyvisa-info

```

This prints diagnostic information for PyVISA, including Machine, Python, backends, etc

```text
Machine Details:
   Platform ID:    Windows
   Processor:      Intel64 Family 6
   ...
PyVISA Version: ...

Backends:
   ni:
      Version: 1.8 (bundled with PyVISA)
      ...
   py:
      Version: 0.2
      ...
  sim:
     Version: 0.3
     Spec version: 1.1

```

