# timeout
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

### timeout

Most VISA I/O calls can use a timeout. When configured, any operation that exceeds the timeout stops and raises an exception. Timeout values are stored per instrument in **milliseconds**.

For all PyVISA objects, a timeout is set with

```python
my_device.timeout = 25000

```

In this example, `my_device` can refer to a device, an interface, or a similar target, and the timeout is configured as 25 seconds. For an **infinite** timeout, assign `None`, `float('+inf')`, or:

```python
del my_device.timeout

```

After that, operations on the resource are allowed to run for however long they need, including indefinitely.

For an **immediate** timeout, use 0 or any negative value. In practice, PyVISA treats any value below 1 as immediate.

