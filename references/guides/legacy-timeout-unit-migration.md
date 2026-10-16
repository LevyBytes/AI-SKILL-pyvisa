# Seconds to milliseconds
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

Historical migration guidance for PyVISA 1.5/1.6. Do not treat the old API names as current entrypoints.

### Seconds to milliseconds

Timeout values are now expressed in milliseconds rather than seconds. This matches other VISA implementations: the C-API, LabVIEW, and .NET all use milliseconds. Using the same unit simplifies migration to PyVISA and makes the rest of the VISA documentation easier to apply.

