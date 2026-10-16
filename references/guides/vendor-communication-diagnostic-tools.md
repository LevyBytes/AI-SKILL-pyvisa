# Using third-party softwares
Context: PyVISA introduction-2; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](installation-and-resource-configuration-index.md)

### Using third-party softwares

National Instruments and Keysight VISA implementations include diagnostic utilities, such as NIMax and Keysight Connection Expert, for investigating communication setup problems.

Both toolsets can start an interactive session with the instrument and let you adjust settings in a GUI, which is often easier. Follow the same general procedure described earlier. If communication works in one of those tools, PyVISA can usually be configured to work too. If it fails there, PyVISA will fail as well.

For serial instruments, whether native or emulated over USB, you can also communicate directly through Putty or Tera Term on Windows, or through CoolTerm, Terminal / screen on macOS.

These basic checks may be enough to get communication working. If they are not, asking for help is fine, but remember that maintainers usually cannot test against the instrument that is failing in your setup.
