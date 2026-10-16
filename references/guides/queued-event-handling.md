# Waiting on events using a queue
Context: PyVISA introduction; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](events-and-visa-shell-index.md)

### Waiting on events using a queue

Start by looking at the queue-based pattern, where the code waits until an event has been placed in a queue.

```python
from pyvisa import ResourceManager, constants

# Requires a PyVISA release supporting the ResourceManager context manager.
with ResourceManager() as rm, rm.open_resource("TCPIP::192.168.0.2::INSTR") as instr:
    event_type = constants.EventType.service_request
    event_mech = constants.EventMechanism.queue
    instr.enable_event(event_type, event_mech)
    try:
        # Replace these commands with the instrument's documented SRQ sequence.
        instr.write("*SRE 1")
        instr.write("INIT")
        response = instr.wait_on_event(event_type, 1000)
        assert not response.timed_out
        assert response.event.event_type == event_type
        del response  # WaitResponse releases the received VISA event context.
    finally:
        instr.disable_event(event_type, event_mech)
```

Review the setup first: to avoid duplicating values, the code saves the desired event type and notification mechanism, then turns event notifications on.

```python
# Type of event we want to be notified about
event_type = constants.EventType.service_request
# Mechanism by which we want to be notified
event_mech = constants.EventMechanism.queue

instr.enable_event(event_type, event_mech)

```

The instrument must then be configured to emit the selected event at the appropriate moment, and the operation that will trigger it must be started. In this example the event is a Service Request event. Service requests are typically enabled for particular register states, with the exact details set by the instrument. Here, the useful case being modeled is a service request raised when an operation has finished.

Last, the code waits for the event and uses a timeout of 1000ms so it cannot block indefinitely. After the event arrives, event handling is disabled.

