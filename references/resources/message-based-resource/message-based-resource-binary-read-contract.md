# MessageBasedResource binary-read parameter contract

Open when checking arguments and results for the [complete binary-reader implementation](message-based-resource-binary-read-implementation.md).

The retained implementation uses `struct.calcsize` for headerless records. Its signature defaults `data_points` to -1; provide a nonnegative count when the response has no length header.

```text
Read values from the device in binary format returning an iterable
        of values.

        Parameters
        ----------
        datatype : BINARY_DATATYPES, optional
            Format string for a single element. See struct module. 'f' by default.
        is_big_endian : bool, optional
            Are the data in big or little endian order. Defaults to False.
        container : Union[Type, Callable[[Iterable], Sequence]], optional
            Container type to use for the output data. Possible values are: list,
            tuple, np.ndarray, etc, Default to list.
        header_fmt : util.BINARY_HEADERS, optional
            Format of the header prefixing the data. Defaults to 'ieee'.
        expect_termination : bool, optional
            When set to False, the expected length of the binary values block
            does not account for the final termination character
            (the read termination). Defaults to True.
        data_points : int, optional
             Number of points expected in the block. This is used only if the
             instrument does not report it itself. This will be converted in a
             number of bytes based on the datatype. Defaults to -1 in the implementation signature.
        chunk_size : int, optional
            Size of the chunks to read from the device. Using larger chunks may
            be faster for large amount of data.
        monitoring_interface : SupportsUpdate Protocol, optional
            Progress monitoring object with update() method that accepts the number
            of bytes read. See the tqdm documentation (a progress bar package) for
            more information.

        Returns
        -------
        Sequence[Union[int, float]]
            Data read from the device.
```

[Source license and checked revision](../../pyvisa-source-license.md).
