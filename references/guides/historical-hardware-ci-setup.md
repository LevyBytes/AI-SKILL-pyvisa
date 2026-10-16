# Continuous integration setup
Context: PyVISA advanced; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](backend-development-index.md)

Historical source context: the platform or CI dates below describe that release period; they are not a current support matrix.

## Continuous integration setup

### Continuous integration setup

Comprehensive PyVISA testing is difficult because it needs both a VISA library implementation and real instruments. Without those pieces, coverage mostly reaches utility code and infrastructure. Those limited tests live at the root of the pyvisa testsuite package and run on every commit through Github Actions together with linters and documentation builds.

Keysight tools made available to PyVISA developers allow most message based resource capabilities to be tested as well. Because the build bots need hardware, those tests cannot run on typical hosted CIs services such as Travis, Azure, Github actions, etc.

A self-hosted builder can execute tests that depend on those tools. PyVISA developer selected Azure Pipelines for self-hosted runners because Azure is simple to use and should keep builder maintenance low while Azure handles the CI service itself. Github Actions was considered too, but for security reason self-hosted runners should not execute on forks, and Github Actions currently offers no way to block self-hosted runners from forked runs.

An Azure self-hosted runner is in place and stays active till December 2020. It can test only TCPIP based resources. A replacement runner is planned for the first trimester of 2021, hopefully adding USB::INSTR and GPIB resource support.

The current runner setup is imperfect, so it may occasionally go offline. If this happen before December 2020, contact @MatthieuDartiailh on Github.

Note

The current runner uses Windows and conda. Because of how Windows activation scripts work, calls to activate or conda activate have to be preceded by call.

