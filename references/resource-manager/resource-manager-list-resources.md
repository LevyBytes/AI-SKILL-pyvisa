# pyvisa.highlevel.ResourceManager.list_resources
Context: PyVISA pyvisa.highlevel.ResourceManager; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](../constants/constants-and-resource-manager-index.md) / [Owning VISA resource class and backend contract](resource-manager.md)

```text
list_resources(query: str = '?*::INSTR') → Tuple[str, ...]
```

Type and source details:

- [str](https://docs.python.org/3/library/stdtypes.html#str)
- [Tuple](https://docs.python.org/3/library/typing.html#typing.Tuple)

Return a tuple containing all connected devices that match query.

Notes

The query uses VISA Resource Regular Expression syntax, which differs from Python regular expression syntax. (see below)

VISA Resource Regular Expression syntax is defined by the VISA Library specification: [http://www.ivifoundation.org/docs/vpp43.pdf](http://www.ivifoundation.org/docs/vpp43.pdf)

Symbol Meaning ———- ———-

? Matches exactly one character.

Makes the following character ordinary rather than special.

For example, a question mark after a backslash (?) matches the literal ? character instead of matching any single character.

[list] Matches one character from the enclosed list. You can

use a hyphen to describe a character range.

[^list] Matches any character outside the enclosed list. You can

also use a hyphen to describe a character range.

- Matches 0 or more repeats of the preceding character or expression.

- Matches 1 or more repeats of the preceding character or expression.

Exp|exp Matches either the expression before or after the operator. The or

operator | applies to the whole expression before or after it, not only to the adjacent character. For example, VXI|GPIB means (VXI)|(GPIB), not VX(I|G)PIB.

(exp) Groups characters or expressions.

Therefore the default query, '?\*::INSTR', matches any character sequence that ends with '::INSTR'.

On some platforms, resources that are already open are omitted.

