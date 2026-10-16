# pyvisa.highlevel.list_backends

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](highlevel-implementation-index.md)

```python
def list_backends() -> List[str]:
    """Return installed backends.

    Backends are installed python packages named pyvisa_<something> where <something>
    is the name of the backend.

    """
    return ["ivi"] + [
        name[7:]
        for (loader, name, ispkg) in pkgutil.iter_modules()
        if (name.startswith("pyvisa_") or name.startswith("pyvisa-"))
        and not name.endswith("-script")
    ]

#: Maps backend name to VisaLibraryBase derived class
_WRAPPERS: Dict[str, Type[VisaLibraryBase]] = {}
```

[Source license and checked revision](../pyvisa-source-license.md).
