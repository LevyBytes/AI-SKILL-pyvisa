# pyvisa.resources.messagebased imports and declarations

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Source context](messagebased-implementation-index.md) / [Source context](messagebased-implementation-index.md)

```python

# -*- coding: utf-8 -*-
"""High level wrapper for MessageBased Instruments.

This file is part of PyVISA.

:copyright: 2014-2024 by PyVISA Authors, see AUTHORS for more details.
:license: MIT, see LICENSE for more details.

"""

import contextlib
import struct
import time
import warnings
from typing import (
    Any,
    Callable,
    Iterable,
    Iterator,
    Optional,
    Protocol,
    Sequence,
    Type,
    Union,
)

from .. import attributes, constants, errors, logger, util
from ..attributes import Attribute
from ..highlevel import VisaLibraryBase
from .resource import Resource
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
