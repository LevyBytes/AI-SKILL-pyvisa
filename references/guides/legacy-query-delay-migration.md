# Removal of Instrument.delay and added Instrument.query_delay
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

Historical migration guidance for PyVISA 1.5/1.6. Do not treat the old API names as current entrypoints.

### Removal of Instrument.delay and added Instrument.query_delay

The original PyVISA implementation lets `Instrument` accept a `delay` argument, adding a pause after each write operation. The same value can also be changed with the `delay` attribute.

In PyVISA 1.6, `delay` was removed, so applications must add delays after write operations themselves. A replacement attribute and argument, `query_delay`, controls the pause between `write` and `read` operations inside `query`. In addition, `query` accepts an optional argument named `delay`, so the value can be changed per method call.

