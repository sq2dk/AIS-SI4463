This is a short presentation of an AIS Transceiver built using an STM32 microcontroller and the Si4463 sub-GHz TRX IC.

![Bottom view of second prototype.](https://github.com/sq2dk/AIS-SI4463/blob/main/ready_PCB.jpg)

The design is very simple, allowing cost reduction and a small footprint.
The STM32F051 was chosen for its compact size, being small enough while still available in an LQFP48 package, which allows easy assembly and testing.
The software was written in C++ using the CubeIDE environment with HAL libraries.

![Bottom view of second prototype.](https://github.com/sq2dk/AIS-SI4463/blob/main/schematic.png)

The Si4463 utilizes the RF front-end design from the datasheet. Although the Si4463 is not capable of handling AIS GMSK packets directly, it detects the AIS training signal and raises an interrupt upon reception. From that point on, it acts as a receiver and modem, while the STM32 handles NRZI encoding, bit-stuffing, checksum calculation, and generates the NMEA sequence of the received packet.
Three element yagi-uda antenna was designed and built, so the receiver together with esp2866 is receiving and sending packets directly to UDP port of AIS servers. The parameters of this station can be viewed on https://www.marinetraffic.com/en/ais/details/stations/19035
![Bottom view of second prototype.](https://github.com/sq2dk/AIS-SI4463/blob/main/AIS_ESP_Antenna.jpg)
![Bottom view of second prototype.](https://github.com/sq2dk/AIS-SI4463/blob/main/on_the_mast.jpg)
AIS transmission was not fully implemented, however ready. Packets were prepared by microcontroller and fed directly to SI4463. Packet handling while transmitting was done by SI4463. No time slot allocation was implemented, thus proces was never finshed, however it was tested and packets sent by this circut were sucesfully received by comecial AIS units.

PCB was designed in KiCad as mostly single-layer board with several traces on the other side (no complnents were placed on back side).


