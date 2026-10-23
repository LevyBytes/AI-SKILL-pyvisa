# pyvisa.constants imports and declarations

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](constants-enumerations-implementation-index.md) / [Source context](constants-enumerations-implementation-index.md) / [Source context](constants-enumerations-implementation-index.md) / [Source context](constants-enumerations-implementation-index.md)

```python

# -*- coding: utf-8 -*-
"""VISA VPP-4.3 constants (VPP-4.3.2 spec, section 3).

Makes all "completion and error codes", "attribute values", "event type
values", and "values and ranges" defined in the VISA specification VPP-4.3.2,
section 3, available as variable values.

The module exports the values under the original, all-uppercase names.

This file is part of PyVISA.

:copyright: 2014-2024 by PyVISA Authors, see AUTHORS for more details.
:license: MIT, see LICENSE for more details.

"""

import enum
import sys

from typing_extensions import Literal

is_64bits = sys.maxsize > 2**32
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
