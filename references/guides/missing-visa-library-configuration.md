# Error: Could not find VISA library
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

### Error: Could not find VISA library

This error means no VISA library path was provided and PyVISA could not locate one automatically. Fix it by creating a configuration file as described in [Configuring the backend](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html#intro-configuring) (recommended), or by passing the library path to the `VisaLibrary` or `ResourceManager` constructor:

```python
>>> visalib = VisaLibrary('/path/to/library')

```

or:

```python
>>> rm = ResourceManager('Path to library')

```

Note

When this error appears while creating a `ResourceManager` from Python built for Cygwin ([https://www.cygwin.com/](https://www.cygwin.com/)) on Windows:

1. Confirm that you are using the Cygwin build of Python by running `python -VV`. Otherwise, use the Windows troubleshooting steps:

```text
$ python -VV
Python 3.9.10 (main, Jan 20 2022, 21:37:52)
[GCC 11.2.0]

```

2. Create a .pyvisarc ([Configuring the backend](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html#intro-configuring)) file and use Cygwin paths with `linux` syntax to point to `visa32.dll` or `visa64.dll`:

```text
$ cat ~/.pyvisarc
[Paths]
VISA library: /cygdrive/c/Windows/System32/visa64.dll

```

or:

```python
rm = pyvisa.ResourceManager('/cygdrive/c/Windows/System32/visa64.dll')

```

or:

```python
rm = pyvisa.ResourceManager('/cygdrive/c/Windows/System32/visa32.dll')

```

