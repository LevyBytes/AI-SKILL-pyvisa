# pyvisa.constants.AddressModifiers

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../constants-enumerations-implementation-index.md) / [Source module imports and declarations](../constants-module-imports-implementation.md)

```python
@enum.unique
class AddressModifiers(enum.IntEnum):
    """Address modifier to be used in high-level register operations."""

    data_private = VI_DATA_PRIV
    data_non_private = VI_DATA_NPRIV
    program_private = VI_PROG_PRIV
    program_non_private = VI_PROG_NPRIV
    block_private = VI_BLCK_PRIV
    block_non_private = VI_BLCK_NPRIV
    d64_private = VI_D64_PRIV
    d64_non_private = VI_D64_NPRIV
    d64_2vme = VI_D64_2EVME
    d64_sst160 = VI_D64_SST160
    d64_sst267 = VI_D64_SST267
    d64_sst320 = VI_D64_SST320
```

[Source license and checked revision](../../pyvisa-source-license.md).
