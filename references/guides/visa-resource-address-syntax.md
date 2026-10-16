# VISA Resource Syntax and Examples
Context: PyVISA introduction-3; retain the exact signature, parameter defaults, return/status contract and backend/protocol qualifiers.
[Source context](addresses-data-and-backends-index.md)

### VISA Resource Syntax and Examples

(This is adapted from the VISA manual)

The table below gives the address-string grammar. Square brackets ([ ]) mark string segments that are optional.

| Interface         | Syntax                                                                                  |
| ----------------- | --------------------------------------------------------------------------------------- |
| ENET-Serial INSTR | ASRL[0]::host address::serial port::INSTR                                               |
| GPIB INSTR        | GPIB[board]::primary address[::secondary address][::INSTR]                              |
| GPIB INTFC        | GPIB[board]::INTFC                                                                      |
| PXI BACKPLANE     | PXI[interface]::chassis number::BACKPLANE                                               |
| PXI INSTR         | PXI[bus]::device[::function][::INSTR]                                                   |
| PXI INSTR         | PXI[interface]::bus-device[.function][::INSTR]                                          |
| PXI INSTR         | PXI[interface]::CHASSISchassis number::SLOTslot number[::FUNCfunction][::INSTR]         |
| PXI MEMACC        | PXI[interface]::MEMACC                                                                  |
| Remote NI-VISA    | visa://host address[:server port]/remote resource                                       |
| Serial INSTR      | ASRLboard[::INSTR]                                                                      |
| TCPIP INSTR       | TCPIP[board]::host address[::LAN device name][::INSTR]                                  |
| TCPIP SOCKET      | TCPIP[board]::host address::port::SOCKET                                                |
| USB INSTR         | USB[board]::manufacturer ID::model code::serial number[::USB interface number][::INSTR] |
| USB RAW           | USB[board]::manufacturer ID::model code::serial number[::USB interface number]::RAW     |
| VXI BACKPLANE     | VXI[board][::VXI logical address]::BACKPLANE                                            |
| VXI INSTR         | VXI[board]::VXI logical address[::INSTR]                                                |
| VXI MEMACC        | VXI[board]::MEMACC                                                                      |
| VXI SERVANT       | VXI[board]::SERVANT                                                                     |

Choose GPIB for communication with GPIB resources. Choose VXI for VXI resources reached through embedded, MXIbus, or 1394 controllers. Choose ASRL for an asynchronous serial device such as RS-232 or RS-485. Choose PXI for PXI and PCI resources. Choose TCPIP when the transport is Ethernet.

The following table shows the default value for optional string segments.

| Optional String Segments | Default Value                      |
| ------------------------ | ---------------------------------- |
| board                    | 0                                  |
| GPIB secondary address   | none                               |
| LAN device name          | inst0                              |
| PXI bus                  | 0                                  |
| PXI function             | 0                                  |
| USB interface number     | lowest numbered relevant interface |

The following table shows examples of address strings:

| Address String                   | Description                                                                                                                                                                                    |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ASRL::1.2.3.4::2::INSTR          | Serial device on port 2 for the ENET Serial controller at address 1.2.3.4.                                                                                                                     |
| ASRL1::INSTR                     | A serial device attached to interface ASRL1.                                                                                                                                                   |
| GPIB::1::0::INSTR                | GPIB device on GPIB interface 0 with primary address 1 and secondary address 0.                                                                                                                |
| GPIB2::INTFC                     | Interface or raw board resource for GPIB interface 2.                                                                                                                                          |
| PXI::15::INSTR                   | PXI device number 15 on bus 0 with implied function 0.                                                                                                                                         |
| PXI::2::BACKPLANE                | Backplane resource for chassis 2 in the default PXI system, where the interface is 0.                                                                                                          |
| PXI::CHASSIS1::SLOT3             | PXI device in slot number 3 in the PXI chassis configured as chassis 1.                                                                                                                        |
| PXI0::2-12.1::INSTR              | PXI bus number 2, device 12 with function 1.                                                                                                                                                   |
| PXI0::MEMACC                     | PXI MEMACC session.                                                                                                                                                                            |
| TCPIP::dev.company.com::INSTR    | TCP/IP device at the given address, accessed through VXI-11 or LXI. It assumes the default LAN Device Name, inst0.                                                                             |
| TCPIP0::1.2.3.4::999::SOCKET     | Raw TCP/IP access to port 999 at the specified IP address.                                                                                                                                     |
| USB::0x1234::125::A22-5::INSTR   | USB Test & Measurement class device identified by manufacturer ID 0x1234, model code 125, and serial number A22-5. It selects the device's first available USBTMC interface, usually number 0. |
| USB::0x5678::0x33::SN999::1::RAW | Raw USB nonclass device identified by manufacturer ID 0x5678, model code 0x33, and serial number SN999. It selects interface number 1 on the device.                                           |
| visa://hostname/ASRL1::INSTR     | The resource ASRL1::INSTR on the specified remote system.                                                                                                                                      |
| VXI::1::BACKPLANE                | Mainframe resource for chassis 1 in the default VXI system, where the interface is 0.                                                                                                          |
| VXI::MEMACC                      | Board-level register access to the VXI interface.                                                                                                                                              |
| VXI0::1::INSTR                   | A VXI device at logical address 1 in VXI interface VXI0.                                                                                                                                       |
| VXI0::SERVANT                    | Servant/device-side resource for VXI interface 0.                                                                                                                                              |

