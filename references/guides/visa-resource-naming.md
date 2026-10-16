# VISA resource names
Context: PyVISA introduction-3; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](addresses-data-and-backends-index.md)

## VISA resource names

### VISA resource names

To connect through [`open_resource()`](https://pyvisa.readthedocs.io/en/latest/api/resourcemanager.html#pyvisa.highlevel.ResourceManager.open_resource), pass the VISA resource name for the desired instrument. In most cases that name begins with the bus type, then the double colon `"::"`, then the instrument's number on that bus. For example,

```none
GPIB::10

```

indicates the GPIB instrument whose number is 10. With two GPIB boards, when the instrument is on board number 1, write

```none
GPIB1::10

```

For the bus portion, valid choices include `"GPIB"`, `"USB"`, and `"ASRL"` (used for a serial/parallel interface). To address an instrument on COM2, use this resource name

```none
ASRL2

```

A serial interface can have only one attached instrument, so no double-colon parameter is included. Still, many VISA implementations accept aliases such as `"COM2"` or `"LPT1"`, and you can define additional aliases yourself.

Resource names ignore case; `"ASRL2"` and `"asrl2"` are equivalent. For deeper details, consult a full VISA reference such as [http://www.ni.com/pdf/manuals/370423a.pdf](http://www.ni.com/pdf/manuals/370423a.pdf).

