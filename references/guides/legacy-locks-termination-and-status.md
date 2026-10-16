# Legacy migration: locks, termination and status access
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md) / [Legacy migration: ResourceManager, discovery and low-level library](legacy-resource-manager-migration.md) / [Legacy migration: timeout units, formatting, delays and aliases](legacy-timeouts-formatting-and-aliases.md)

**If you are doing::**

```python
>>> vpp43.lock(session)

```

change it to:

```python
>>> lib.lock(session)

```

or better:

```python
>>> resource.lock()

```

**If you are doing::**

```python
>>> inst.term_chars = '\r'

```

change it to:

```python
>>> inst.read_termination = '\r'
>>> inst.write_termination = '\r'

```

**If you are doing::**

```python
>>> print(lib.status)

```

change it to:

```python
>>> print(lib.last_status)

```

or even better, do it per resource:

```python
>>> print(rm.last_status) # for the resource manager
>>> print(inst.last_status) # for a specific instrument

```

