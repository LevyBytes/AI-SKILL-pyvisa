# Legacy migration: timeout units, formatting, delays and aliases
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md) / [Legacy migration: ResourceManager, discovery and low-level library](legacy-resource-manager-migration.md) / [Legacy migration: locks, termination and status access](legacy-locks-termination-and-status.md)

**If you are doing::**

```python
>>> inst.timeout = 1  # Seconds

```

change it to:

```python
>>> inst.timeout = 1000  # Milliseconds

```

The preceding code mostly makes several details explicit. It adds 1 line of code, instantiating the ResourceManager object, which is a minor cost for a cleaner result.

When code uses `printf`, `queryf`, `scanf`, `sprintf` or `sscanf` from `vpp43`, replace those calls with pure Python code, as shown below.

If you were using `Instrument.delay`, change your code or use `Instrument.query_delay` (see below).

A few alias has been created to ease the transition:

- ask -> query

- ask_delay -> query_delay

- get_instrument -> open_resource

