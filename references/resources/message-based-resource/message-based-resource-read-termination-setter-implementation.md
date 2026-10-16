# pyvisa.resources.messagebased.MessageBasedResource.read_termination

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](messagebased-implementation-index.md) / [Enclosing source class declaration](message-based-resource-implementation.md) / [Source module imports and declarations](messagebased-module-imports-implementation.md)

```python
    @read_termination.setter
    def read_termination(self, value: Optional[str]) -> None:
        if value:
            # termination character, the rest is just used for verification
            # after each read operation.
            last_char = value[-1:]
            # Consequently, it's illogical to have the real termination
            # character twice in the sequence (otherwise reading would stop
            # prematurely).

            if last_char in value[:-1]:
                raise ValueError("ambiguous ending in termination characters")

            self.set_visa_attribute(
                constants.ResourceAttribute.termchar, ord(last_char)
            )
            self.set_visa_attribute(
                constants.ResourceAttribute.termchar_enabled, constants.VI_TRUE
            )
        else:
            # The termchar is also used in VI_ATTR_ASRL_END_IN (for serial
            # termination) so return it to its default.
            self.set_visa_attribute(constants.ResourceAttribute.termchar, ord(self.LF))
            self.set_visa_attribute(
                constants.ResourceAttribute.termchar_enabled, constants.VI_FALSE
            )

        self._read_termination = value
```

[Source license and checked revision](../../pyvisa-source-license.md).
