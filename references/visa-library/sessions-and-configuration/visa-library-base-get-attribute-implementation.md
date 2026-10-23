# pyvisa.highlevel.VisaLibraryBase.get_attribute

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../backends/highlevel-implementation-index.md) / [Enclosing source class declaration](../visa-library-base-implementation.md)

```python
    def get_attribute(
        self,
        session: Union[VISASession, VISAEventContext, VISARMSession],
        attribute: Union[constants.ResourceAttribute, constants.EventAttribute],
    ) -> Tuple[Any, StatusCode]:
        """Retrieves the state of an attribute.

        Corresponds to viGetAttribute function of the VISA library.

        Parameters
        ----------
        session : Union[VISASession, VISAEventContext]
            Unique logical identifier to a session, event, or find list.
        attribute : Union[constants.ResourceAttribute, constants.EventAttribute]
            Resource or event attribute for which the state query is made.

        Returns
        -------
        Any
            State of the queried attribute for a specified resource
        StatusCode
            Return value of the library call.

        """
        raise NotImplementedError
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
