# Event handling
Context: PyVISA introduction; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](events-and-visa-shell-index.md)

## Event handling

### Event handling

With VISA, an instrument can emit events, most often after a register changes, and the controller can process them through either of two mechanisms:

- storing the events in a queue

- invoking a handler function that was registered for the event when that event is raised

PyVISA can use both mechanisms and exposes a practical interface for each one. The examples below show the two approaches with a fictional instrument.

