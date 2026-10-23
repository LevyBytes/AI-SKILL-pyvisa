# pyvisa.highlevel imports and declarations declaration and imports

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](highlevel-implementation-index.md) / [Source context](highlevel-implementation-index.md) / [Source context](highlevel-implementation-index.md) / [Source context](highlevel-implementation-index.md) / [Source context](highlevel-implementation-index.md) / [Source context](highlevel-implementation-index.md)

```python

# -*- coding: utf-8 -*-
"""High level Visa library wrapper.

This file is part of PyVISA.

:copyright: 2014-2024 by PyVISA Authors, see AUTHORS for more details.
:license: MIT, see LICENSE for more details.

"""

import atexit
import contextlib
import copy
import os
import pkgutil
import warnings
from collections import defaultdict
from importlib import import_module
from itertools import chain
from types import ModuleType
from typing import (
    TYPE_CHECKING,
    Any,
    Callable,
    ContextManager,
    Dict,
    Iterable,
    Iterator,
    List,
    NamedTuple,
    Optional,
    Set,
    SupportsBytes,
    Tuple,
    Type,
    TypeVar,
    Union,
    cast,
)
from weakref import WeakMethod, WeakSet, WeakValueDictionary

from typing_extensions import ClassVar, DefaultDict, Literal

from . import attributes, constants, errors, logger, rname
from .constants import StatusCode
from .typing import (
    VISAEventContext,
    VISAHandler,
    VISAJobID,
    VISAMemoryAddress,
    VISARMSession,
    VISASession,
)
from .util import DebugInfo, LibraryPath

if TYPE_CHECKING:
    from .resources import Resource  # pragma: no cover
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
