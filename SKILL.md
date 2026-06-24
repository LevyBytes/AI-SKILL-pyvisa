---
name: pyvisa
description: Use when working with PyVISA - the Python library for controlling measurement instruments over VISA (GPIB, USB, serial/RS-232, TCPIP/Ethernet): ResourceManager, listing/opening resources, read/write/query, VISA attributes and constants, termination characters, timeouts, event handling, the visa shell, backends (pyvisa-py, NI-VISA), and the high-level/low-level API. import pyvisa. Not for the Python stdlib or other instrument-control libraries.
---

# PyVISA Reference

Original-prose reference for PyVISA, split into one focused file per subject across 54 reference files.
Identifiers (API/type/function names, flags, paths, enums, numbers) are preserved verbatim.

## When to use this

Use this skill when the task involves the PyVISA library for instrument control over VISA - opening a ResourceManager, listing/opening resources (GPIB/USB/serial/TCPIP), read/write/query, VISA attributes and constants, termination characters, timeouts, event handling, the visa shell, choosing a backend (pyvisa-py vs NI-VISA), and the high-level/low-level API.

## Workflow

1. Open `references/INDEX.md` (or `references/topics.json`) and pick the one file that matches.
2. Read only that file; open another only if the task spans subjects. Grep across files when needed: `rg -n "PATTERN" references/*.md`.
3. Treat every identifier as an exact reference fact — never invent or paraphrase.

## Gotchas

Recurring failure modes and what to do instead live in the sibling [GOTCHA.md](GOTCHA.md).

## References

All depth lives in `references/` — start at `references/INDEX.md`, metadata in `references/topics.json`. One subject per file.

## Source

Adapted from the upstream PyVISA documentation into original prose for local reference. Identifiers remain verbatim. Upstream: https://pyvisa.readthedocs.io/en/latest/

## Verification

```powershell
python D:\dev\SKILLS\skills\skill-drafting\scripts\validate_skill_package.py D:\dev\SKILLS\skills\pyvisa
```
