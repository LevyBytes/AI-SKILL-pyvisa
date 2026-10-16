# Error: No matching architecture
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

### Error: No matching architecture

This error appears when the Python architecture and VISA architecture do not match.

Note

PyVISA attempts to parse the underlying foreign function library error and turn it into a clearer message. When parsing fails, PyVISA shows the original error instead.

In Mac OS X the original error message looks like this:

```text
OSError: dlopen(/Library/Frameworks/visa.framework/visa, 6): no suitable image found.  Did find:
    /Library/Frameworks/visa.framework/visa: no matching architecture in universal wrapper
    /Library/Frameworks/visa.framework/visa: no matching architecture in universal wrapper

```

In Linux the original error message looks like this:

```text
OSError: Could not open VISA library:
    Error while accessing /usr/local/vxipnp/linux/bin/libvisa.so.7:/usr/local/vxipnp/linux/bin/libvisa.so.7: wrong ELF class: ELFCLASS32

```

Start by using this debug command to inspect the installation details:

```console
pyvisa-info

```

The output shows the architecture used to compile the Python interpreter and, near the end, the VISA libraries that PyVISA found.

The solution is to:

1. Install and use a VISA library matching your Python architecture

Download and install it from **National Instruments's VISA**, then run the debug command again to check whether PyVISA found the new library. If it still is not found, create a configuration file as described in [Configuring the backend](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html#intro-configuring).

If a VISA library with the correct bitness is not available, use solution 2.

or

1. Install and use a Python matching your VISA library architecture

On Windows and Linux, download and install Python with the matching bitness, then rerun your script with the new Python.

In macOS, Python is usually delivered as universal binary (x86_64 and arm).

You can run it in x86_64 mode by running:

```console
arch -x86_64 python myscript.py

```

or in arm mode by running:

```console
arch -arm64 python myscript.py

```

You can create an alias by adding the following line

`alias pythonx86="arch -x86_64 python"`

Add it to the startup file for your shell, such as .bashrc, .profile, ~/.bash_profile, or the equivalent file your shell reads.

You can also create a [virtual environment](http://www.virtualenv.org/en/latest/) for this.

