---
layout: page
title: "TFSIK02: High-power wireless telemetry data link"
permalink: /avionics/TFSIK02/
parent: "Communication & Interfaces"
nav_order: "11"
---

# TFSIK02 - High-Power Telemetry Modem

### Purchasing Information

The device can be purchased from [ThunderFly s.r.o.](https://www.thunderfly.cz/). Contact us by email at sale@thunderfly.cz for a commercial quotation. We are the designers of this modem and therefore have full control of the modem's construction and design. This gives us the ability to react even to non-standard requests for modification or functions.

## Overview

The SiK Telemetry Radio is a small, light, and inexpensive open-source radio platform that typically allows ranges significantly better than one kilometer with a basic whip antenna kit. The range can be extended to several kilometers using a directional antenna on the ground. This radio is plug-and-play with all Pixhawk Standard and other flight controllers, providing the easiest way to set up a telemetry connection between the UAV and a ground control station. It uses open-source firmware specially designed to work well with MAVLink packets and to integrate with Mission Planner, Ardupilot, QGroundControl, and PX4 Autopilot.

The TFSIK02 is a state-of-the-art SiK-based UAV telemetry modem incorporating dual antenna diversity and exceptional resistance to noise. This open-source hardware solution employs the advanced [Si1060](https://www.silabs.com/documents/public/data-sheets/Si106x-8x.pdf) chip from the Si10xx series and is further enhanced by the Si4463 EZRadioPRO transceiver, ensuring robust and secure communication capabilities. The modem's design prioritizes immunity to interference from out-of-band frequencies, guaranteeing reliable performance in challenging environments and securing its position as a top choice for UAV systems that demand the utmost data integrity and security.

### Key Features

- **Plug-n-play** for Pixhawk Standard Flight Controllers. The easiest way to connect your Autopilot in the airframe with the Ground Station 
- **Superior Noise Immunity**: With a hardware-optimized RF front-end, the modem excels in environments plagued by out-of-band signal interference. The feature applies to multiple frequency bands.
- **Robust Hardware Design**: Housed in a customizable 3D printed enclosure with electromagnetic shielding, it promises both durability and adaptability.
- **Antenna Diversity**: Employs dual external antennas via MCX connectors, enhancing connectivity flexibility across different frequency bands requiring different antenna systems.
- **Cutting-Edge Communication Technologies**:
  - Implements Frequency-Hopping Spread Spectrum (FHSS)
  - Utilizes Adaptive Time Division Multiplexing (TDM) with Configurable duty cycle
  - Supports Listen Before Talk (LBT) and Adaptive Frequency Agility (AFA)
  - Error correction corrects up to 25% of bit errors
  - [AES-256](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) or another encryption available upon request.
- **High-Performance Metrics**:
  - Offers a transparent serial link
  - Facilitates air data rates reaching up to 250kbps
  - Integrates MAVLink protocol framing and status reporting
  - Achieves several kilometers of range with a small whip antenna
- **Open-Source and Highly Configurable**: Loaded with SiK firmware for enhanced customization through AT and RT commands, it supports the MAVLink 2 protocol, Configurable through Mission Planner & APM Planner

## Hardware Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| Frequency range | 142 MHz - 1050 MHz | The Exact frequency band has to be set by the factory|
| RF power range | 20dBm to 35dBm | Adjustable by AT commands |
| Input Noise Figure | 0.6 dB |  LNA noise figure |
| OIP3 |  39.5dBm | Input LNA gain 18.7dB|
| Receiver sensitivity|  -117 dBm or better | Depends on datalink bandwidth configuration |
| Bandwidth |  < 4 MHz | RF filter selective |
| RF connectors| [MCX](https://en.wikipedia.org/wiki/MCX_connector) on both RF ports | snap-on function prevents damage of connector by extensive external forces|
| Serial interface| 3.3 V UART | 6-position JST-GH connector with [handshake available](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter) |
| Operating and storage temperature | −20°C to +40°C | Limited by case material |
| Operational power voltage | +5V to +5.4V, 500mA max | Undervoltage is not treated. Current consumption is defined mainly by the set RF power. Receive current is 25 mA|
| Mass | 18g | Including the housing |
| Dimensions | 55x10x35mm | Housing dimensions |
| Weather resistance | [IP40](https://en.wikipedia.org/wiki/IP_Code) | External connectors fully occupied |

### LEDs Indicators Status 

The radios have 3 status LEDs: red, orange, and green

- Green LED blinking - searching for another radio
- Green LED solid - link is established with another radio
- Red LED flashing - transmitting data
- Red LED solid - in firmware update mode
- Orange LED solid or dim indicates the selected antenna port 

### Applications

The TFSIK01 is designed precisely for UAV command and control applications, ensuring dependable, long-distance communication links between UAVs and ground control stations. It is also highly effective in ROS2 environments for robotics, providing a reliable long-range wireless datalink.

The modem was originally developed to transmit atmospheric data measured in real time using the [TF-ATMON system](https://docs.thunderfly.cz/instruments/TF-ATMON).

### Installation and Configuration

Integration into UAV systems is straightforward, requiring only a [Pixhawk-compatible JST-GH UART connection](https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf). The side placement of external antennas, connected through MCX connectors, is specifically selected to increase robustness and ease of installation.

## Hardware setup

{: .warning }
Like most RF devices, the TFSIK01 must not be operated without a properly connected and matched antenna. Doing so can damage the RF output stage.

### Connecting to Autopilot

Connection to the autopilot flight controller is facilitated through a JST-GH cable with a 6-pin connector. While PX4 firmware initially configures the TELEM1 port for telemetry connections, adjustments in the PX4 or Ardupilot firmware settings allow for modem connections through any available UART port. 

### Ground Station Connectivity

#### Direct UART Connection

The TFSIK01 modem directly interfaces with ground stations via its UART port, enabling easy integration with Raspberry Pi or similar single-board computers equipped with 3.3V UART outputs. This direct connection method is ideal for configurations demanding low latency and direct data control.

#### USB Connectivity

To connect the modem to a computer, a USB to UART conversion is essential. The [TFUSBSERIAL01 module](/avionics/TFUSBSERIAL01), specifically designed for this purpose, features an FTDI-based USB chip for reliable data transmission and includes a USB-C connector for easy linking to computers or mobile devices, alongside a UART JST-GH connector for straightforward connection to the TFSIK01 modem.


### Frequency Options

ThunderFly typically configures the TFSIK02 modem for the 433 and 868 MHz bands. For alternative frequency requests, ThunderFly can customize the modem to meet specific applications. For detailed information on frequency adjustments, contact ThunderFly directly at [sale@thunderfly.cz](mailto:sale@thunderfly.cz).


