# Pxi, Usb

> Pyvisa reference. Original prose; identifiers preserved verbatim.

## Overview

Covers source listings for pyvisa.resources.pxi and pyvisa.resources.usb.

## Source code for pyvisa.resources.pxi

### Source code for pyvisa.resources.pxi

```

# -*- coding: utf-8 -*-
"""High level wrapper for pxi resources.

This file is part of PyVISA.

:copyright: 2014-2024 by PyVISA Authors, see AUTHORS for more details.
:license: MIT, see LICENSE for more details.

"""

from .. import attributes, constants
from ..attributes import Attribute
from .registerbased import RegisterBasedResource
from .resource import Resource

@Resource.register(constants.InterfaceType.pxi, "BACKPLANE")
class PXIBackplane(RegisterBasedResource):
    """Communicates with to devices of type PXI[interface]::BACKPLANE

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    #: Manufacturer name.
    manufacturer_name: Attribute[str] = attributes.AttrVI_ATTR_MANF_NAME()

    #: Model name of the device.
    model_name: Attribute[str] = attributes.AttrVI_ATTR_MODEL_NAME()

class PXICommon(RegisterBasedResource):
    """Common parent class for PXI INSTR and MEMACC resources."""

    #: Number of elements by which to increment the source offset after a transfer.
    source_increment: Attribute[int] = attributes.AttrVI_ATTR_SRC_INCREMENT()

    #: Number of elements by which to increment the destination offset after a transfer.
    destination_increment: Attribute[int] = attributes.AttrVI_ATTR_DEST_INCREMENT()

    #: Should I/O accesses use DMA (True) or Programmed I/O (False).
    allow_dma: Attribute[bool] = attributes.AttrVI_ATTR_DMA_ALLOW_EN()

[docs]
@Resource.register(constants.InterfaceType.pxi, "INSTR")
class PXIInstrument(PXICommon):
    """Communicates with to devices of type PXI::<device>[::INSTR]

    More complex resource names can be specified with the following grammar:
        PXI[bus]::device[::function][::INSTR]
    or:
        PXI[interface]::bus-device[.function][::INSTR]
    or:
        PXI[interface]::CHASSISchassis number::SLOTslot number[::FUNCfunction][::INSTR]

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    #: Manufacturer name.
    manufacturer_name: Attribute[str] = attributes.AttrVI_ATTR_MANF_NAME()

    #: Manufacturer identification number of the device.
    manufacturer_id: Attribute[int] = attributes.AttrVI_ATTR_MANF_ID()

    #: Model name of the device.
    model_name: Attribute[str] = attributes.AttrVI_ATTR_MODEL_NAME()

    #: Model code for the device.
    model_code: Attribute[int] = attributes.AttrVI_ATTR_MODEL_CODE()

[docs]
@Resource.register(constants.InterfaceType.pxi, "MEMACC")
class PXIMemory(PXICommon):
    """Communicates with to devices of type PXI[interface]::MEMACC

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

```

## Source code for pyvisa.resources.usb

### Source code for pyvisa.resources.usb

```

# -*- coding: utf-8 -*-
"""High level wrapper for USB resources.

This file is part of PyVISA.

:copyright: 2014-2024 by PyVISA Authors, see AUTHORS for more details.
:license: MIT, see LICENSE for more details.

"""

from .. import attributes, constants
from ..attributes import Attribute
from .messagebased import ControlRenMixin, MessageBasedResource

class USBCommon(MessageBasedResource):
    """Common class for USB resources."""

    #: USB interface number used by the given session.
    interface_number: Attribute[int] = attributes.AttrVI_ATTR_USB_INTFC_NUM()

    #: USB serial number of this device.
    serial_number: Attribute[str] = attributes.AttrVI_ATTR_USB_SERIAL_NUM()

    #: USB protocol used by this USB interface.
    usb_protocol: Attribute[int] = attributes.AttrVI_ATTR_USB_PROTOCOL()

    #: Maximum size of data that will be stored by any given USB interrupt.
    maximum_interrupt_size: Attribute[int] = attributes.AttrVI_ATTR_USB_MAX_INTR_SIZE()

    #: Manufacturer name.
    manufacturer_name: Attribute[str] = attributes.AttrVI_ATTR_MANF_NAME()

    #: Manufacturer identification number of the device.
    manufacturer_id: Attribute[int] = attributes.AttrVI_ATTR_MANF_ID()

    #: Model name of the device.
    model_name: Attribute[str] = attributes.AttrVI_ATTR_MODEL_NAME()

    #: Model code for the device.
    model_code: Attribute[int] = attributes.AttrVI_ATTR_MODEL_CODE()

[docs]
@MessageBasedResource.register(constants.InterfaceType.usb, "INSTR")
class USBInstrument(ControlRenMixin, USBCommon):
    """USB INSTR resources USB::manufacturer ID::model code::serial number

    More complex resource names can be specified with the following grammar:
        USB[board]::manufacturer ID::model code::serial number[::USB interface number][::INSTR]

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

    #: Whether the device is 488.2 compliant.
    is_4882_compliant: Attribute[bool] = attributes.AttrVI_ATTR_4882_COMPLIANT()

[docs]
    def control_in(
        self,
        request_type_bitmap_field: int,
        request_id: int,
        request_value: int,
        index: int,
        length: int = 0,
    ) -> bytes:
        """Performs a USB control pipe transfer from the device.

        Parameters
        ----------
        request_type_bitmap_field : int
            bmRequestType parameter of the setup stage of a USB control transfer.
        request_id : int
            bRequest parameter of the setup stage of a USB control transfer.
        request_value : int
            wValue parameter of the setup stage of a USB control transfer.
        index : int
            wIndex parameter of the setup stage of a USB control transfer.
            This is usually the index of the interface or endpoint.
        length : int
            wLength parameter of the setup stage of a USB control transfer.
            This value also specifies the size of the data buffer to receive
            the data from the optional data stage of the control transfer.

        Returns
        -------
        bytes
            The data buffer that receives the data from the optional data stage
            of the control transfer.

        """
        return self.visalib.usb_control_in(
            self.session,
            request_type_bitmap_field,
            request_id,
            request_value,
            index,
            length,
        )[0]

[docs]
    def control_out(
        self,
        request_type_bitmap_field: int,
        request_id: int,
        request_value: int,
        index: int,
        data: bytes = b"",
    ):
        """Performs a USB control pipe transfer to the device.

        Parameters
        ----------
        request_type_bitmap_field : int
            bmRequestType parameter of the setup stage of a USB control transfer.
        request_id : int
            bRequest parameter of the setup stage of a USB control transfer.
        request_value : int
            wValue parameter of the setup stage of a USB control transfer.
        index : int
            wIndex parameter of the setup stage of a USB control transfer.
            This is usually the index of the interface or endpoint.
        data : bytes
            The data buffer that sends the data in the optional data stage of
            the control transfer.

        """
        return self.visalib.usb_control_out(
            self.session,
            request_type_bitmap_field,
            request_id,
            request_value,
            index,
            data,
        )

[docs]
@MessageBasedResource.register(constants.InterfaceType.usb, "RAW")
class USBRaw(USBCommon):
    """USB RAW resources: USB::manufacturer ID::model code::serial number::RAW

    More complex resource names can be specified with the following grammar:
        USB[board]::manufacturer ID::model code::serial number[::USB interface number]::RAW

    Do not instantiate directly, use
    :meth:`pyvisa.highlevel.ResourceManager.open_resource`.

    """

```
