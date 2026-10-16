# pyvisa.resources.gpib imports and declarations

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json)

```python



# -*- coding: utf-8 -*-
"""High level wrapper for GPIB resources.

This file is part of PyVISA.

:copyright: 2014-2024 by PyVISA Authors, see AUTHORS for more details.
:license: MIT, see LICENSE for more details.

"""

from enum import Enum
from time import perf_counter
from typing import Tuple

from .. import attributes, constants
from ..attributes import Attribute
from .messagebased import ControlRenMixin, MessageBasedResource
from .resource import Resource
```

[Source license and checked revision](../../pyvisa-source-license.md).
