# pyvisa.resources.messagebased.MessageBasedResource

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
class MessageBasedResource(Resource):
    """Base class for resources that use message based communication."""

    CR: str = "\r"
    LF: str = "\n"

    #: Number of bytes to read at a time. Some resources (serial) may not support
    #: large chunk sizes.
    chunk_size: int = 20 * 1024

    #: Delay in s to sleep between the write and read occuring in a query
    query_delay: float = 0.0

    #: Internal storage for the read_termination character
    _read_termination: Optional[str] = None

    #: Internal storage for the write_termination character
    _write_termination: str = CR + LF

    #: Internal storage for the encoding
    _encoding: str = "ascii"
```

[Source license and checked revision](../../pyvisa-source-license.md).
