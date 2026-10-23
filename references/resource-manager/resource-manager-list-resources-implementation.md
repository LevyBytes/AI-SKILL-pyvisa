# pyvisa.highlevel.ResourceManager.list_resources

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../backends/highlevel-implementation-index.md) / [Source context](../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](resource-manager-implementation.md)

```python
    def list_resources(self, query: str = "?*::INSTR") -> Tuple[str, ...]:
        r"""Return a tuple of all connected devices matching query.

        Notes
        -----
        The query uses the VISA Resource Regular Expression syntax - which is
        not the same as the Python regular expression syntax. (see below)

        The VISA Resource Regular Expression syntax is defined in the VISA
        Library specification:
        http://www.ivifoundation.org/docs/vpp43.pdf

        Symbol      Meaning
        ----------  ----------

        ?           Matches any one character.

        \           Makes the character that follows it an ordinary character
                    instead of special character. For example, when a question
                    mark follows a backslash (\?), it matches the ? character
                    instead of any one character.

        [list]      Matches any one character from the enclosed list. You can
                    use a hyphen to match a range of characters.

        [^list]     Matches any character not in the enclosed list. You can use
                    a hyphen to match a range of characters.

        *           Matches 0 or more occurrences of the preceding character or
                    expression.

        +           Matches 1 or more occurrences of the preceding character or
                    expression.

        Exp|exp     Matches either the preceding or following expression. The or
                    operator | matches the entire expression that precedes or
                    follows it and not just the character that precedes or follows
                    it. For example, VXI|GPIB is interpreted as (VXI)|(GPIB),
                    rather than VX(I|G)PIB.

        (exp)       Grouping characters or expressions.

        Thus the default query, '?*::INSTR', matches any sequences of characters
        ending ending with '::INSTR'.

        On some platforms, devices that are already open are not returned.

        """

        return self.visalib.list_resources(self.session, query)
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
