# Migrating, Faq, Getting Nivisa

> Pyvisa reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Frequently asked questions; migration notes for PyVISA < 1.5; miscellaneous questions; NI-VISA Installation.

## Frequently asked questions

### Frequently asked questions

This section answers common PyVISA questions. It begins with miscellaneous questions, then moves to questions that need more detailed explanations.

- [Miscellaneous questions](https://pyvisa.readthedocs.io/en/latest/faq/faq.html)
  - [Is PyVISA endorsed by National Instruments?](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#is-pyvisa-endorsed-by-national-instruments)
  - [Who makes PyVISA\_?](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#who-makes-pyvisa)
  - [Is PyVISA thread-safe?](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#is-pyvisa-thread-safe)
  - [I have an error in my program and I am having trouble to fix it](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#i-have-an-error-in-my-program-and-i-am-having-trouble-to-fix-it)
  - [I found a bug, how can I report it?](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#i-found-a-bug-how-can-i-report-it)
  - [Error: Image not found](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#error-image-not-found)
  - [Error: Could not find VISA library](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#error-could-not-find-visa-library)
  - [Error: No matching architecture](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#error-no-matching-architecture)
  - [OSError: Could not open VISA library: function ‘viOpen’ not found](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#oserror-could-not-open-visa-library-function-viopen-not-found)
  - [VisaIOError: VI_ERROR_SYSTEM_ERROR: Unknown system error:](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#visaioerror-vi-error-system-error-unknown-system-error)
  - [Where can I get more information about VISA?](https://pyvisa.readthedocs.io/en/latest/faq/faq.html#where-can-i-get-more-information-about-visa)

- [NI-VISA Installation](https://pyvisa.readthedocs.io/en/latest/faq/getting_nivisa.html)
  - [Mac OS X](https://pyvisa.readthedocs.io/en/latest/faq/getting_nivisa.html#mac-os-x)
  - [Windows](https://pyvisa.readthedocs.io/en/latest/faq/getting_nivisa.html#windows)
  - [Linux](https://pyvisa.readthedocs.io/en/latest/faq/getting_nivisa.html#linux)

- [Migrating from PyVISA < 1.5](https://pyvisa.readthedocs.io/en/latest/faq/migrating.html)
  - [Short summary](https://pyvisa.readthedocs.io/en/latest/faq/migrating.html#short-summary)
  - [A more detailed description](https://pyvisa.readthedocs.io/en/latest/faq/migrating.html#a-more-detailed-description)

## Migrating from PyVISA < 1.5

### Migrating from PyVISA < 1.5

Note

For PyVISA 1.4 compatibility, use PyVISA 1.5. It adds Python 3 support, improved visa library detection heuristics, support for Windows, Linux and OS X, and removes the singleton object. PyVISA 1.6+ introduces several compatibility breaks.

The `visalib` package, included with [Lantz](https://lantz.readthedocs.org/), influenced some of these choices.

### Short summary

Through the legacy module, PyVISA 1.5 remains fully compatible with earlier PyVISA releases, although parts of the underlying implementation changed. To follow current development and stay compatible with PyVISA > 1.5, a few usage patterns should be updated.

PyVISA 1.6 does break compatibility, but those changes enable several useful improvements.

**If you are doing:**

```python
>>> import pyvisa
>>> keithley = pyvisa.instrument("GPIB::12")
>>> print(keithley.ask("*IDN?"))

```

change it to:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager()
>>> keithley = rm.open_resource("GPIB::12")
>>> print(keithley.query("*IDN?"))

```

**If you are doing:**

```python
>>> print(pyvisa.get_instruments_list())

```

change it to:

```python
>>> print(rm.list_resources())

```

**If you are doing:**

```python
>>> import pyvisa.vpp43 as vpp43
>>> vpp43.visa_library.load_library("/path/to/my/libvisa.so.7")

```

change it to:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager("/path/to/my/libvisa.so.7")
>>> lib = rm.visalib

```

**If you are doing::**

```python
>>> vpp43.lock(session)

```

change it to:

```python
>>> lib.lock(session)

```

or better:

```python
>>> resource.lock()

```

**If you are doing::**

```python
>>> inst.term_chars = '\r'

```

change it to:

```python
>>> inst.read_termination = '\r'
>>> inst.write_termination = '\r'

```

**If you are doing::**

```python
>>> print(lib.status)

```

change it to:

```python
>>> print(lib.last_status)

```

or even better, do it per resource:

```python
>>> print(rm.last_status) # for the resource manager
>>> print(inst.last_status) # for a specific instrument

```

**If you are doing::**

```python
>>> inst.timeout = 1  # Seconds

```

change it to:

```python
>>> inst.timeout = 1000  # Milliseconds

```

The preceding code mostly makes several details explicit. It adds 1 line of code, instantiating the ResourceManager object, which is a minor cost for a cleaner result.

When code uses `printf`, `queryf`, `scanf`, `sprintf` or `sscanf` from `vpp43`, replace those calls with pure Python code, as shown below.

If you were using `Instrument.delay`, change your code or use `Instrument.query_delay` (see below).

A few alias has been created to ease the transition:

>

-

ask -> query

-

ask_delay -> query_delay

-

get_instrument -> open_resource

### A more detailed description

### Dropped support for string related functions

The VISA library provides routines for searching and manipulating strings, including `printf`, `queryf`, `scanf`, `sprintf` and `sscanf`. That is natural because VISA workflows do a lot of string handling. Early PyVISA wrapped those routines, but the same operations are simple to express in pure python and were seldom used.

For backwards compatibility, PyVISA 1.5 still includes these functions; 1.6 removes them.

We suggest that you replace such functions by a pure Python version.

### Isolated low-level wrapping module

Earlier PyVISA placed the low level implementation (`vpp43`) together with higher level constructs. ctypes handled the wrapping of the VISA library.

In 1.5, that layer became `ctwrapper`. Separating the foreign function calls lets us test them apart from higher level abstractions. It also makes it possible to create new low level modules that high level modules can use as drop in replacements for `ctwrapper`.

In 1.6, `ResourceManager` became the object presented to users. The `VisaLibrary` type can be selected from `library_path` and obtained from a plugin package.

We have two of such packages planned:

-

a Mock module for testing a PyVISA program on systems where VISA is not installed.

-

a wrapper based on CFFI. CFFI is a new python package for wrapping foreign libraries more easily and more robustly. It may become part of Python in the future.

To support migration, PyVISA 1.5 keeps `vpp43` in the legacy subpackage, reimplemented on top of `ctwrapper`. In 1.6, that module is removed.

Every function formerly available in `vpp43` is now available in `ctwrapper`, with one added first argument: the foreign library wrapper.

The recommended replacement for `vpp43` is to use the `VisaLibrary` object stored on the resource manager's visalib attribute; it exposes all foreign functions as bound methods, as shown below.

### No singleton objects

The first PyVISA design used singleton-style globals: `visa_library` for the library wrapper, as an instance of the old `pyvisa.vpp43.VisaLibrary`, and `resource_manager` for the resource manager, as an instance of the old `pyvisa.visa.ResourceManager`. Importing the package created them. A user could point to another library with `load_library`, but that call did not update `resource_manager`, so the two globals could become inconsistent.

A few other globals also existed, including `status`, which kept the most recent status returned by the library, plus the warning context used to suppress unwanted warnings.

Version 1.5 adds a `VisaLibrary` class and a `ResourceManager` class, both located in `pyvisa.highlevel`. These classes are not strict singletons. Multiple `VisaLibrary` and `ResourceManager` instances are possible, provided they point to different foreign libraries. In code, this means:

```python
>>> lib1 = pyvisa.VisaLibrary("/path/to/my/libvisa.so.7")
>>> lib2 = pyvisa.VisaLibrary("/path/to/my/libvisa.so.7")
>>> lib3 = pyvisa.VisaLibrary("/path/to/my/libvisa.so.8")
>>> lib1 is lib2
True
>>> lib1 is lib3
False

```

Usually you need a `ResourceManager` rather than direct access to a `VisaLibrary` object. You can do:

```python
>>> lib = pyvisa.VisaLibrary("/path/to/my/libvisa.so.7")
>>> rm = lib.resource_manager

```

or equivalently:

```python
>>> rm = pyvisa.ResourceManager("/path/to/my/libvisa.so.7")

```

Note

When no library path is supplied, PyVISA gets it from the user settings file, if that file exists, or otherwise guesses from the OS.

In 1.6, library status is tracked for each resource. Warnings can also be silenced per resource, and `last_status` exposes the stored status.

All together, these changes makes PyVISA thread safe.

### VisaLibrary methods as way to call Visa functions

Originally, PyVISA's `VisaLibrary` class mainly held a reference to the ctypes library plus a small set of functions.

Version 1.5 added the new `VisaLibrary` class (`pyvisa.highlevel`). It exposes every low level function defined in `ctwrapper` as a bound method, so code can call it this way:

```python
>>> import pyvisa
>>> rm = pyvisa.ResourceManager("/path/to/my/libvisa.so.7")
>>> lib = rm.visalib
>>> print(lib.read_stb(session))

```

(In most cases this is unnecessary, because the resource should already provide the function you need)

It also exposes every VISA foreign function from the underlying library as a static method, which lets you write code like this:

```python
>>> status = ctypes.c_ushort()
>>> ret lib.viReadSTB(session, ctypes.byref(status))
>>> print(ret.value)

```

### Ask vs. query

PyVISA formerly used `ask` for a `write` followed by a `read`. Many other programs call that same operation `query`, so the name was changed while an alias remains for migration.

However, `ask_for_values` is not an alias for `query_values`, since the API differs. `ask_for_values` remains on the old formatting API, which is limited and broken. Migrate code to `query_values`.

### Seconds to milliseconds

Timeout values are now expressed in milliseconds rather than seconds. This matches other VISA implementations: the C-API, LabVIEW, and .NET all use milliseconds. Using the same unit simplifies migration to PyVISA and makes the rest of the VISA documentation easier to apply.

### Removal of Instrument.delay and added Instrument.query_delay

The original PyVISA implementation lets `Instrument` accept a `delay` argument, adding a pause after each write operation. The same value can also be changed with the `delay` attribute.

In PyVISA 1.6, `delay` was removed, so applications must add delays after write operations themselves. A replacement attribute and argument, `query_delay`, controls the pause between `write` and ``read` operations inside `query`. In addition, `query` accepts an optional argument named `query`, so the value can be changed per method call.

### Deprecated term_chars and automatic removal of CR + LF

In the original PyVISA implementation, `Instrument` takes a `term_chars` argument to change at the read and write termination characters. If this argument is `None`, `CR + LF` is appended to each outgoing message and not expected for incoming messages (although removed if present).

In PyVISA 1.6, `term_chars` is replaced by `read_termination` and ``write_termination`. In this way, you can set independently the termination for each operation. Automatic removal of `CR + LF` is also gone in 1.6.

## Miscellaneous questions

### Miscellaneous questions

### Is PyVISA endorsed by National Instruments?

No. PyVISA is an independent project from National Instrument, implemented as a wrapper around the VISA library.

### Who makes PyVISA\_?

Torsten Bronger and Gregor Thalhammer wrote the first PyVISA implementation, building on Thalhammer's earlier experience.

From March 2012 to August 2013, Florian Bauer maintained it. From August 2013 to December 2017, maintenance was handled by Hernan E. Grecco <[hernan.grecco@gmail.com](mailto:hernan.grecco%40gmail.com)>. The current maintainer is Matthieu Dartiailh <[m.dartiailh@gmail.com](mailto:m.dartiailh%40gmail.com)>.

Take a look at [AUTHORS](https://github.com/pyvisa/pyvisa/blob/main/AUTHORS) for more information

### Is PyVISA thread-safe?

Yes, PyVISA is thread safe starting from version 1.6.

### I have an error in my program and I am having trouble to fix it

PyVISA can log operations in a useful way. Add these commands to your program, then run it again:

```python
import pyvisa
pyvisa.log_to_screen()

```

### I found a bug, how can I report it?

Report it on the [Issue Tracker](https://github.com/pyvisa/pyvisa/issues) and include the operating system, python version, and library version. You can also add supporting details by pasting the output from this command:

```python
pyvisa-info

```

### Error: Image not found

This error means the VISA library path is invalid. Verify the path passed to the constructor or set in the configuration file.

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

>

1.

Confirm that you are using the Cygwin build of Python by running `python -VV`. Otherwise, use the Windows troubleshooting steps:

```python
$ python -VV
Python 3.9.10 (main, Jan 20 2022, 21:37:52)
[GCC 11.2.0]

```

2.

Create a .pyvisarc ([Configuring the backend](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html#intro-configuring)) file and use Cygwin paths with `linux` syntax to point to `visa32.dll` or `visa64.dll`:

```python
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

### Error: No matching architecture

This error appears when the Python architecture and VISA architecture do not match.

Note

PyVISA attempts to parse the underlying foreign function library error and turn it into a clearer message. When parsing fails, PyVISA shows the original error instead.

In Mac OS X the original error message looks like this:

```python
OSError: dlopen(/Library/Frameworks/visa.framework/visa, 6): no suitable image found.  Did find:
    /Library/Frameworks/visa.framework/visa: no matching architecture in universal wrapper
    /Library/Frameworks/visa.framework/visa: no matching architecture in universal wrapper

```

In Linux the original error message looks like this:

```python
OSError: Could not open VISA library:
    Error while accessing /usr/local/vxipnp/linux/bin/libvisa.so.7:/usr/local/vxipnp/linux/bin/libvisa.so.7: wrong ELF class: ELFCLASS32

```

Start by using this debug command to inspect the installation details:

```python
pyvisa-info

```

The output shows the architecture used to compile the Python interpreter and, near the end, the VISA libraries that PyVISA found.

The solution is to:

>

1.

Install and use a VISA library matching your Python architecture

Download and install it from **National Instruments's VISA**, then run the debug command again to check whether PyVISA found the new library. If it still is not found, create a configuration file as described in [Configuring the backend](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html#intro-configuring).

If a VISA library with the correct bitness is not available, use solution 2.

or

>

1.

Install and use a Python matching your VISA library architecture

On Windows and Linux, download and install Python with the matching bitness, then rerun your script with the new Python.

In macOS, Python is usually delivered as universal binary (x86_64 and arm).

You can run it in x86_64 mode by running:

```python
arch -x86_64 python myscript.py

```

or in arm mode by running:

```python
arch -arm64 python myscript.py

```

You can create an alias by adding the following line

>

alias pythonx86=”arch -x86_64 python”

Add it to the startup file for your shell, such as .bashrc, .profile, ~/.bash_profile, or the equivalent file your shell reads.

You can also create a [virtual environment](http://www.virtualenv.org/en/latest/) for this.

### OSError: Could not open VISA library: function ‘viOpen’ not found

On Windows, Python 3.8 changed how .dll files are loaded (see [https://docs.python.org/3/whatsnew/3.8.html#bpo-36085-whatsnew](https://docs.python.org/3/whatsnew/3.8.html#bpo-36085-whatsnew)). Because of that change, some Keysight VISA releases cannot locate required .dll dependencies during loading. To fix it, create a configuration file and set dll_extra_paths, as covered in [Configuring the backend](https://pyvisa.readthedocs.io/en/latest/introduction/configuring.html#intro-configuring).

### VisaIOError: VI_ERROR_SYSTEM_ERROR: Unknown system error:

When creating a pyvisa.ResourceManager object fails, turn on screen logging with pyvisa.log_to_screen() first so you can confirm whether the dll files are found. If the dlls are located correctly, the failure may resemble: \* viOpenDefaultRM('<ViObject object at 0x000002B6CA4658C8>',) -> -1073807360. In the linked report, reinstalling python fixed the problem, suggesting that ctypes may have been damaged. [[https://github.com/pyvisa/pyvisa/issues/538](https://github.com/pyvisa/pyvisa/issues/538)]

### Where can I get more information about VISA?

-

The original VISA docs:

-

[VISA specification](http://www.ivifoundation.org/Downloads/Specifications.htm) (scroll down to the end)

-

[VISA library specification](http://www.ivifoundation.org/Downloads/Class%20Specifications/vpp43.doc)

-

[VISA specification for textual languages](http://www.ivifoundation.org/Downloads/Class%20Specifications/vpp432.doc)

-

The very good VISA manuals from [National Instruments’s VISA](http://ni.com/visa/):

-

[NI-VISA User Manual](http://digital.ni.com/manuals.nsf/websearch/266526277DFF74F786256ADC0065C50C)

-

[NI-VISA Programmer Reference Manual](http://digital.ni.com/manuals.nsf/websearch/87E52268CF9ACCEE86256D0F006E860D)

-

[NI-VISA help file](http://digital.ni.com/manuals.nsf/websearch/21992F3750B967ED86256F47007B00B3) in HTML

## NI-VISA Installation

### NI-VISA Installation

For any OS, use the same bitness for NI-VISA and Python, whether 32- or 64-bit. Install an NI-VISA release supported on your OS, then use a Python build with the bitness that matches that NI-VISA installation.

PyVISA provides a debug command that can help diagnose this issue and related setup problems:

```python
pyvisa-info

```

National Instruments lists NI VISA **17.5** support for these platforms.

Note

When your system is not supported by NI-VISA, consult the [Frequently asked questions](https://pyvisa.readthedocs.io/en/latest/faq/index.html#faq).

### Mac OS X

Download [NI-VISA for Mac OS X](http://www.ni.com/download/ni-visa-17.5/7224/en/)

Supports:

-

Mac OS X 10.7.x x86 and x86-64

-

Mac OS X 10.8.x

Only certain instrumentation buses support 64-bit VISA applications: ENET-Serial, USB, and TCPIP. NI I/O Trace cannot log VISA operations from 64-bit VISA applications.\_

### Windows

Download [NI-VISA for Windows](http://www.ni.com/download/ni-visa-17.5/7220/en/)

Suports:

-

Windows Server 2003 R2 (32-bit version only)

-

Windows Server 2008 R2 (64-bit version only)

-

Windows 8 x64 Edition (64-bit version)

-

Windows 8 (32-bit version)

-

Windows 7 x64 Edition (64-bit version)

-

Windows 7 (32-bit version)

-

Windows Vista x64 Edition (64-bit version)

-

Windows Vista (32-bit version)

-

Windows XP Service Pack 3

Windows Server 2003 R2 support can depend on turning off physical address extensions (PAE).\_

### Linux

Download [NI-VISA for Linux](http://www.ni.com/download/ni-visa-17.0/6700/en/)

Supports:

-

openSUSE 12.2

-

openSUSE 12.1

-

Red Hat Enterprise Linux Desktop + Workstation 6

-

Red Hat Enterprise Linux Desktop + Workstation 5

-

Scientific Linux 6.x

-

Scientific Linux 5.x

More details details can be found in the [README](http://download.ni.com/support/softlib//visa/NI-VISA/17.0/Linux/README.txt) of the installer.

Note

NI-VISA can be used on additional linux distributions, but setup is less straightforward. For Arch linux and related distributions, the AUR package [ni-visa](https://aur.archlinux.org/packages/ni-visa/) (early development) has working reports for USB and TCPIP interfaces. Restart after installation so the setup takes effect.
