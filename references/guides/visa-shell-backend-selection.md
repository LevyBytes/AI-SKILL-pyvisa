# PyVisa Shell Backends
Context: PyVISA introduction; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](events-and-visa-shell-index.md)

### PyVisa Shell Backends

If the desired backend is available (check with the `info` command), the shell can be switched away from the default backend using `-b BACKEND` or `--backend BACKEND`.

You can invoke:

```console
pyvisa-shell -b sim

```

This selects pyvisa-sim rather than the default backend, which is useful when testing a pyvisa-sim configuration.

You can include a specific file to use for the simulated backend:

```console
pyvisa-shell -b file.yaml@sim

```

You can invoke:

```console
pyvisa-shell -b py

```

This selects pyvisa-py instead of the ivi backend for cases where ivi is not installed.

