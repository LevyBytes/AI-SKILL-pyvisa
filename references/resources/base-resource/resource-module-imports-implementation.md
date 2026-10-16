# pyvisa.resources.resource imports and declarations

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](resource-implementation-index.md)

```python


# -*- coding: utf-8 -*-
"""High level wrapper for a Resource.

This file is part of PyVISA.

:copyright: 2014-2024 by PyVISA Authors, see AUTHORS for more details.
:license: MIT, see LICENSE for more details.

"""

import contextlib
import time
from functools import update_wrapper
from typing import (
    Any,
    Callable,
    ContextManager,
    Iterator,
    Optional,
    Set,
    Type,
    TypeVar,
    Union,
    cast,
)

from typing_extensions import ClassVar, Literal

from .. import attributes, constants, errors, highlevel, logger, rname, typing, util
from ..attributes import Attribute
from ..events import Event
from ..typing import VISAEventContext, VISAHandler, VISASession
```

[Source license and checked revision](../../pyvisa-source-license.md).
