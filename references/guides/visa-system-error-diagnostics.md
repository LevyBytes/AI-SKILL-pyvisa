# VisaIOError: VI_ERROR_SYSTEM_ERROR: Unknown system error:
Context: PyVISA faq; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](troubleshooting-and-legacy-migration-index.md)

### VisaIOError: VI_ERROR_SYSTEM_ERROR: Unknown system error:

When creating a pyvisa.ResourceManager object fails, turn on screen logging with pyvisa.log_to_screen() first so you can confirm whether the dll files are found. If the dlls are located correctly, the failure may resemble: \* viOpenDefaultRM('<ViObject object at 0x000002B6CA4658C8>',) -> -1073807360. In the linked report, reinstalling python fixed the problem, suggesting that ctypes may have been damaged. [[https://github.com/pyvisa/pyvisa/issues/538](https://github.com/pyvisa/pyvisa/issues/538)]

