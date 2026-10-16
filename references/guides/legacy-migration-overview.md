# Migrating from PyVISA < 1.5
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

## Migrating from PyVISA < 1.5

### Migrating from PyVISA < 1.5

Note

For PyVISA 1.4 compatibility, use PyVISA 1.5. It adds Python 3 support, improved visa library detection heuristics, support for Windows, Linux and OS X, and removes the singleton object. PyVISA 1.6+ introduces several compatibility breaks.

The `visalib` package, included with [Lantz](https://lantz.readthedocs.org/), influenced some of these choices.

