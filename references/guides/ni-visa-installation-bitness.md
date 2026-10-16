# NI-VISA Installation
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

## NI-VISA Installation

### NI-VISA Installation

For any OS, use the same bitness for NI-VISA and Python, whether 32- or 64-bit. Install an NI-VISA release supported on your OS, then use a Python build with the bitness that matches that NI-VISA installation.

PyVISA provides a debug command that can help diagnose this issue and related setup problems:

```console
pyvisa-info

```

National Instruments lists NI VISA **17.5** support for these platforms.

Note

When your system is not supported by NI-VISA, consult the [Frequently asked questions](https://pyvisa.readthedocs.io/en/latest/faq/index.html#faq).

