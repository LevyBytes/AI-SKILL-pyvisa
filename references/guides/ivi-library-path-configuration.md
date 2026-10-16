# Configuring the IVI backend
Context: PyVISA introduction-3; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](addresses-data-and-backends-index.md)

### Configuring the IVI backend

Note

The IVI backend requires an IVI-VISA library to be installed first. NI-VISA is one option, but another IVI-VISA library can be used. For NI-VISA details, see ([NI-VISA Installation](https://pyvisa.readthedocs.io/en/latest/faq/getting_nivisa.html#faq-getting-nivisa)).

PyVISA usually locates the shared visa library without extra configuration. When autodetection fails, or when a different library should be selected, pass the library path to the [`ResourceManager`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager) constructor:

```python
>>> rm = ResourceManager('Path to library')

```

To make this library the default for every PyVISA application, put the setting in a `.pyvisarc` file (including the leading dot) in your [home directory](http://en.wikipedia.org/wiki/Home_directory).

| Operating System          | Location                                   |
| ------------------------- | ------------------------------------------ |
| Windows NT                | `<root>\WINNT\Profiles\<username>`         |
| Windows 2000, XP and 2003 | `<root>\Documents and Settings\<username>` |
| Windows Vista, 7 or 8     | `<root>\Users\<username>`                  |
| Mac OS X                  | `/Users/<username>`                        |
| Linux                     | `/home/<username>` (depends on the distro) |

On Windows XP, for instance, place the file in the "Documents and Settings" user folder; if your login account is "smith", the path would be `C:\Documents and Settings\smith\.pyvisarc`.

The file uses INI syntax. For instance, when the library resides at `/usr/lib/libvisa.so.7`, `.pyvisarc` should include this content:

```ini
[Paths]

VISA library: /usr/lib/libvisa.so.7

```

Please note that [Paths] is treated case-sensitively.

On Windows, additional .dll lookup directories can be supplied with a .pyvisarc file using this pattern:

```ini
[Paths]

dll_extra_paths: C:\Program Files\Keysight\IO Libraries Suite\bin;C:\Program Files (x86)\Keysight\IO Libraries Suite\bin

```

A site-wide configuration file may be placed at `/usr/share/pyvisa/.pyvisarc` (`/usr/local/...` is another possibility, depending on where Python is installed). On Windows, the usual location is `c:\Python37\share\pyvisa\.pyvisarc`.

When a problem comes up, consult the [Frequently asked questions](https://pyvisa.readthedocs.io/en/latest/faq/index.html#faq). That page covers common fixes and practical debugging techniques. If nothing resolves the issue, open a report in the [issue tracker](https://github.com/pyvisa/pyvisa/issues)

