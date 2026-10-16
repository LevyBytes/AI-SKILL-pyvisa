# pyvisa.highlevel.VisaLibraryBase.map_address
Context: PyVISA pyvisa.highlevel.VisaLibraryBase; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../visa-library-base-low-level-api-index.md) / [Owning VISA resource class and backend contract](../visa-library-base.md)

```text
map_address(
    session: VISASession,
    map_space: AddressSpace,
    map_base: int,
    map_size: int,
    access: Literal[False] = False,
    suggested: int | None = None,
) → Tuple[int, StatusCode]
```

Type and source details:

- [int](https://docs.python.org/3/library/functions.html#int)
- [Literal](https://docs.python.org/3/library/typing.html#typing.Literal)
- [None](https://docs.python.org/3/library/constants.html#None)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)
- [StatusCode](https://pyvisa.readthedocs.io/en/latest/api/constants.html#pyvisa.constants.StatusCode)

Maps the specified memory space into the process’s address space.

Corresponds to viMapAddress function of the VISA library.

Parameters:

- **session** (VISASession) – Unique logical identifier to a session.

- **map_space** (constants.AddressSpace) – Specifies the address space to map.

- **map_base** ([int](https://docs.python.org/3/library/functions.html#int)) – Offset (in bytes) of the memory to be mapped.

- **map_size** ([int](https://docs.python.org/3/library/functions.html#int)) – Amount of memory to map (in bytes).

- **access** (False) – Unused parameter.

- **suggested** (Optional[[int](https://docs.python.org/3/library/functions.html#int)], optional) – If not None, the operating system attempts to map memory at the specified address. That address is not guaranteed; this operation may instead place the mapping in a different address region than the suggested one.

Returns:

- int – Address in your process space where the memory was mapped

- StatusCode – Return value of the library call.

