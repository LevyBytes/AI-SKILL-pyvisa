# Dropped support for string related functions
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

Historical migration guidance for PyVISA 1.5/1.6. Do not treat the old API names as current entrypoints.

### A more detailed description

### Dropped support for string related functions

The VISA library provides routines for searching and manipulating strings, including `printf`, `queryf`, `scanf`, `sprintf` and `sscanf`. That is natural because VISA workflows do a lot of string handling. Early PyVISA wrapped those routines, but the same operations are simple to express in pure python and were seldom used.

For backwards compatibility, PyVISA 1.5 still includes these functions; 1.6 removes them.

We suggest that you replace such functions by a pure Python version.

