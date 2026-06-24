# PyVISA — Gotchas

Recurring failure modes when relying on the PyVISA reference, and what to do instead. Read alongside `SKILL.md`.

- Treat every identifier (class/method/attribute name, VISA constant, resource string like 'GPIB0::14::INSTR', enum value) as an exact reference fact - do not invent or paraphrase the API.
- These docs track PyVISA's latest version; verify version-sensitive behavior, defaults, and deprecations against the installed pyvisa version.
- PyVISA requires a VISA backend - pyvisa-py (pure Python) or a vendor library (NI-VISA, Keysight, etc.). Available resources, attributes, and behavior depend on the backend plus installed instrument drivers, not on PyVISA alone.
- Some autodoc API pages are long, structure-light dumps split into parts; use references/INDEX.md or `rg -n "PATTERN" references/*.md` to locate a symbol rather than reading a whole part file.
