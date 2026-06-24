# Highlevel (part 2) (5)

> Pyvisa reference. Original prose; identifiers preserved verbatim.

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

[docs]
def list_resources_info(self, query: str = "?\*::INSTR") -> Dict[str, ResourceInfo]:
"""Get extended information about all connected devices matching query.

        For details of the VISA Resource Regular Expression syntax used in query,
        refer to list_resources().

        Returns
        -------
        Dict[str, ResourceInfo]
            Mapping of resource name to ResourceInfo

        """

        return {
            resource: self.resource_info(resource)
            for resource in self.list_resources(query)
        }

    def list_opened_resources(self) -> List["Resource"]:
        """Return a list of all the opened resources."""
        opened = []
        for resource in self.created_resources:
            try:
                resource.session
            except errors.InvalidSession:
                pass
            else:
                opened.append(resource)
        return opened

[docs]
def resource_info(self, resource_name: str, extended: bool = True) -> ResourceInfo:
"""Get the (extended) information of a particular resource.

        Parameters
        ----------
        resource_name : str
            Unique symbolic name of a resource.
        extended : bool, optional
            Also get extended information (ie. resource_class, resource_name, alias)

        """

        if extended:
            ret, err = self.visalib.parse_resource_extended(
                self.session, resource_name
            )
        else:
            ret, err = self.visalib.parse_resource(self.session, resource_name)

        return ret

[docs]
def open_bare_resource(
self,
resource_name: str,
access_mode: constants.AccessModes = constants.AccessModes.no_lock,
open_timeout: int = constants.VI_TMO_IMMEDIATE,
) -> Tuple[VISASession, StatusCode]:
"""Open the specified resource without wrapping into a class.

        Parameters
        ----------
        resource_name : str
            Name or alias of the resource to open.
        access_mode : constants.AccessModes, optional
            Specifies the mode by which the resource is to be accessed,
            by default constants.AccessModes.no_lock
        open_timeout : int, optional
            If the ``access_mode`` parameter requests a lock, then this
            parameter specifies the absolute time period (in milliseconds) that
            the resource waits to get unlocked before this operation returns an
            error, by default constants.VI_TMO_IMMEDIATE.

        Returns
        -------
        VISASession
            Unique logical identifier reference to a session.
        StatusCode
            Return value of the library call.

        """
        return self.visalib.open(self.session, resource_name, access_mode, open_timeout)

[docs]
def open_resource(
self,
resource_name: str,
access_mode: constants.AccessModes = constants.AccessModes.no_lock,
open_timeout: int = constants.VI_TMO_IMMEDIATE,
resource_pyclass: Optional[Type["Resource"]] = None,
\*\*kwargs: Any,
) -> "Resource":
"""Return an instrument for the resource name.

        Parameters
        ----------
        resource_name : str
            Name or alias of the resource to open.
        access_mode : constants.AccessModes, optional
            Specifies the mode by which the resource is to be accessed,
            by default constants.AccessModes.no_lock
        open_timeout : int, optional
            If the ``access_mode`` parameter requests a lock, then this
            parameter specifies the absolute time period (in milliseconds) that
            the resource waits to get unlocked before this operation returns an
            error, by default constants.VI_TMO_IMMEDIATE.
        resource_pyclass : Optional[Type[Resource]], optional
            Resource Python class to use to instantiate the Resource.
            Defaults to None: select based on the resource name.
        kwargs : Any
            Keyword arguments to be used to change instrument attributes
            after construction.

        Returns
        -------
        Resource
            Subclass of Resource matching the resource.

        """
        if resource_pyclass is None:
            info = self.resource_info(resource_name, extended=True)

            try:
                # When using querying extended resource info the resource_class is not
                # None
                resource_pyclass = self.resource_classes[
                    (info.interface_type, info.resource_class)  # type: ignore
                ]
            except KeyError:
                resource_pyclass = self.resource_classes[
                    (constants.InterfaceType.unknown, "")
                ]
                logger.warning(
                    "There is no class defined for %r. Using Resource",
                    (info.interface_type, info.resource_class),
                )
        if hasattr(self.visalib, "open_resource"):
            res = self.visalib.open_resource(  # type: ignore
                resource_name, access_mode, open_timeout, resource_pyclass, **kwargs
            )
        else:
            res = resource_pyclass(self, resource_name)
            for key in kwargs.keys():
                try:
                    getattr(res, key)
                    present = True
                except AttributeError:
                    present = False
                except errors.InvalidSession:
                    present = True

                if not present:
                    raise ValueError(
                        "%r is not a valid attribute for type %s"
                        % (key, res.__class__.__name__)
                    )

            res.open(access_mode, open_timeout)

            for key, value in kwargs.items():
                setattr(res, key, value)

        self.created_resources.add(res)

        return res

```

```
