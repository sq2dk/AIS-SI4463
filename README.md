This is a short presentation of an AIS Transceiver built using an STM32 microcontroller and the Si4463 sub-GHz TRX IC.

The design is very simple, allowing cost reduction and a small footprint.
The STM32F051 was chosen for its compact size, being small enough while still available in an LQFP48 package, which allows easy assembly and testing.
The software was written in C++ using the CubeIDE environment with HAL libraries.

The Si4463 utilizes the RF front-end design from the datasheet. Although the Si4463 is not capable of handling AIS GMSK packets directly, it detects the AIS training signal and raises an interrupt upon reception. From that point on, it acts as a receiver and modem, while the STM32 handles NRZI encoding, bit-stuffing, checksum calculation, and generates the NMEA sequence of the received packet.
