# pyvisa.highlevel.VisaLibraryBase.__new__

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def __new__(
        cls: Type[T], library_path: Union[str, LibraryPath] = ""
    ) -> "VisaLibraryBase":
        """Create a new VISA library from the specified path.

        If a library was already created using the same path and class this
        library object is returned instead.

        Parameters
        ----------
        library_path : str | LibraryPath
            Path to the VISA library to use in the backend.

        Raises
        ------
        OSError
            Raised if the VISA library object could not be created.

        """
        if library_path == "":
            errs = []
            for path in cls.get_library_paths():
                try:
                    return cls(path)
                except OSError as e:
                    logger.debug("Could not open VISA library %s: %s", path, str(e))
                    errs.append(str(e))
                except Exception as e:
                    errs.append(str(e))
            else:
                raise OSError("Could not open VISA library:\n" + "\n".join(errs))

        if not isinstance(library_path, LibraryPath):
            lib_path = LibraryPath(library_path, "user specified")
        else:
            lib_path = library_path

        if (cls, lib_path) in cls._registry:
            return cls._registry[(cls, lib_path)]

        obj = super(VisaLibraryBase, cls).__new__(cls)

        obj.library_path = lib_path

        obj._logging_extra = {"library_path": obj.library_path}

        obj._init()

        # Create instance specific registries.
        #: Error codes on which to issue a warning.
        obj.issue_warning_on = set(errors.default_warnings)
        obj._last_status_in_session = {}
        obj._ignore_warning_in_session = defaultdict(set)
        obj.handlers = defaultdict(list)
        obj.resource_manager = None

        logger.debug("Created library wrapper for %s", lib_path)

        cls._registry[(cls, lib_path)] = obj

        return obj
```

[Source license and checked revision](../../pyvisa-source-license.md).
