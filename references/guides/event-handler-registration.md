# Registering handlers for event
Context: PyVISA introduction; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](events-and-visa-shell-index.md)

### Registering handlers for event

Instead of blocking until an event arrives, some workflows should react as soon as the event is raised; for those cases, direct invocation of a function by the VISA library is useful. Here is the pattern.

Note

One can enable event handling using both mechanisms (`constants.EventMechanism.all`)

```python
from time import monotonic, sleep
from pyvisa import ResourceManager, constants

def handle_event(resource, event, user_handle):
    resource.called = True
    print(f"Handled event {event.event_type} on {resource}")

# Requires a PyVISA release supporting the ResourceManager context manager.
with ResourceManager() as rm, rm.open_resource("TCPIP::192.168.0.2::INSTR") as instr:
    instr.called = False
    event_type = constants.EventType.service_request
    event_mech = constants.EventMechanism.handler
    wrapped = instr.wrap_handler(handle_event)
    user_handle = instr.install_handler(event_type, wrapped, 42)
    try:
        instr.enable_event(event_type, event_mech, None)
        # Replace these commands with the instrument's documented SRQ sequence.
        instr.write("*SRE 1")
        instr.write("INIT")
        deadline = monotonic() + 10
        while not instr.called:
            if monotonic() >= deadline:
                raise TimeoutError("No service request arrived within 10 seconds")
            sleep(0.05)
    finally:
        try:
            instr.disable_event(event_type, event_mech)
        finally:
            instr.uninstall_handler(event_type, wrapped, user_handle)
```

A handler must use the signature VISA expects: (session, event_type, event_context, user_handle). That raw callback shape is awkward because it exposes low-level values such as session, the VISA resource ID, and event_context, which plays the corresponding role for events. To present a cleaner handler API, call [`wrap_handler`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource.wrap_handler) on the [`Resource`](https://pyvisa.readthedocs.io/en/latest/api/resources.html#pyvisa.resources.Resource) instance. After wrapping, the function should use this signature: (resource, event, user_handle), matching the handler used here:

```python
def handle_event(resource, event, user_handle):
    resource.called = True
    print(f"Handled event {event.event_type} on {resource}")

```

And before installing the handler, we wrap it:

```python
wrapped = instr.wrap_handler(handle_event)

```

Wrap the handler with the same resource that will later receive the installation. Also keep the wrapped handler object, because that exact object is needed when removing the handler.

Next we install the handler and enable the event processing:

```python
user_handle = instr.install_handler(event_type, wrapped, 42)
instr.enable_event(event_type, event_mech, None)

```

While installing a handler, you may provide a user handle that is forwarded to the callback. The handle helps distinguish which registration fired when the same handler has been installed more than once on one resource. A backend may convert this value, so the value delivered to the callback can differ from the one originally registered, and its concrete representation is backend dependent. Keep the converted value returned by install handler so the handler can be removed later.

Note

For the ctwrapper included with PyVISA, the backend maps the value to a matching ctypes object, such as c_float for a float or c_int for an integer, etc

