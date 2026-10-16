# Deprecated term_chars and automatic removal of CR + LF
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

Historical migration guidance for PyVISA 1.5/1.6. Do not treat the old API names as current entrypoints.

### Deprecated term_chars and automatic removal of CR + LF

In the original PyVISA implementation, `Instrument` takes a `term_chars` argument to change at the read and write termination characters. If this argument is `None`, `CR + LF` is appended to each outgoing message and not expected for incoming messages (although removed if present).

In PyVISA 1.6, `term_chars` is replaced by `read_termination` and `write_termination`. In this way, you can set independently the termination for each operation. Automatic removal of `CR + LF` is also gone in 1.6.

