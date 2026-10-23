# pyvisa.resources.tcpip imports and declarations

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json)

```python



# -*- coding: utf-8 -*-
"""High level wrapper for TCPIP resources.

This file is part of PyVISA.

:copyright: 2014-2024 by PyVISA Authors, see AUTHORS for more details.
:license: MIT, see LICENSE for more details.

"""

from .. import constants
from .messagebased import ControlRenMixin, MessageBasedResource
from .resource import Resource
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
