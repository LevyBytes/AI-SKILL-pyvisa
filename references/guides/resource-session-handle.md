# session
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

### Attributes of Resource

### session

Every instrument communication channel owns a distinct session handle, and you can retrieve that value:

```python
>>> my_device.session
10442240

```

If the resource is closed, an exception will be raised:

```python
>>> inst.close()
>>> inst.session
Traceback (most recent call last):
...
pyvisa.errors.InvalidSession: Invalid session handle. The resource might be closed.

```

