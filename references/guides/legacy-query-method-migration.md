# Ask vs. query
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

Historical migration guidance for PyVISA 1.5/1.6. Do not treat the old API names as current entrypoints.

### Ask vs. query

PyVISA formerly used `ask` for a `write` followed by a `read`. Many other programs call that same operation `query`, so the name was changed while an alias remains for migration.

However, `ask_for_values` is not an alias for `query_values`, since the API differs. `ask_for_values` remains on the old formatting API, which is limited and broken. Migrate code to `query_values`.

