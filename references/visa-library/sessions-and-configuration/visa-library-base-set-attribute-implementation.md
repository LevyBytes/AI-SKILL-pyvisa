# pyvisa.highlevel.VisaLibraryBase.set_attribute

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def set_attribute(
        self,
        session: VISASession,
        attribute: constants.ResourceAttribute,
        attribute_state: Any,
    ) -> StatusCode:
        """Set the state of an attribute.

        Corresponds to viSetAttribute function of the VISA library.

        Parameters
        ----------
        session : VISASession
            Unique logical identifier to a session.
        attribute : constants.ResourceAttribute
            Attribute for which the state is to be modified.
        attribute_state : Any
            The state of the attribute to be set for the specified object.

        Returns
        -------
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source license and checked revision](../../pyvisa-source-license.md).
