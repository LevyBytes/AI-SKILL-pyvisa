# I have an error in my program and I am having trouble to fix it
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

### I have an error in my program and I am having trouble to fix it

PyVISA can log operations in a useful way. Add these commands to your program, then run it again:

```python
import pyvisa
pyvisa.log_to_screen()

```

