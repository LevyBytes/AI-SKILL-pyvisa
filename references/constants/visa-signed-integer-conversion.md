# pyvisa.constants._to_int

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](constants-enumerations-implementation-index.md) / [Source module imports and declarations](constants-module-imports-implementation.md)

```python
def _to_int(x: int) -> int:
    """Convert a signed completion and error code to the proper value.

    This function is necessary because the VISA specification is flawed: It defines
    the VISA codes, which have a value less than zero, in their internal 32-bit
    signed integer representation. However, this is positive.  ctypes doesn't
    care about that and (correctly) returns the negative value, which is left as
    such by Python.

    Parameters
    ----------
    x : int
        Value in 32-bit notation as listed in the VPP-4.3.2 specification

    Returns
    -------
    int
        Properly signed value

    """
    if x > 0x7FFFFFFF:
        return int(x - 0x100000000)
    else:
        return int(x)


# fmt: off

# ======================================================================================
# --- VISA constants  ------------------------------------------------------------------
# ======================================================================================

# Status codes : success
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
