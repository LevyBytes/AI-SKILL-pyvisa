# pyvisa.resources.gpib.GPIBInstrument.wait_for_srq

Implementation excerpt: read with the linked module imports and owning class. This is not a standalone module.
[Source context](../../implementation-modules.json) / [Enclosing source class declaration](gpib-instrument-implementation.md) / [Source module imports and declarations](../gpib/gpib-module-imports-implementation.md)

```python
    def wait_for_srq(self, timeout: int = 25000) -> None:
        """Wait for a Service Request (SRQ) coming from the instrument.

        Note that this method is not ended when *another* instrument signals an
        SRQ, only *this* instrument.

        Parameters
        ----------
        timeout : int
            Maximum waiting time in milliseconds. Defaul: 25000 (milliseconds).
            None means waiting forever if necessary.

        """
        self.enable_event(
            constants.EventType.service_request, constants.EventMechanism.queue
        )

        if timeout and not (0 <= timeout <= 4294967295):
            raise ValueError("timeout value is invalid")

        starting_time = perf_counter()

        while True:
            if timeout is None:
                adjusted_timeout = constants.VI_TMO_INFINITE
            else:
                adjusted_timeout = int(
                    (starting_time + timeout / 1e3 - perf_counter()) * 1e3
                )
                if adjusted_timeout < 0:
                    adjusted_timeout = 0

            self.wait_on_event(constants.EventType.service_request, adjusted_timeout)
            if self.stb & 0x40:
                break

        self.discard_events(
            constants.EventType.service_request, constants.EventMechanism.queue
        )
```

[Source at the checked PyVISA revision](https://github.com/pyvisa/pyvisa/tree/843d62a50cac9a23e7585c5135f3fd5eb9470f17).
