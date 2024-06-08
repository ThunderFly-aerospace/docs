---
layout: page
title: "TFSIK01: High-reliable wireless telemetry data link"
permalink: /avionics/TFSIK01/
parent: Avionics
nav_order: "10"
---

# TFSIK01 - High-Performance Telemetry Modem

### Overview

The SiK Telemetry Radio is a small, light, and inexpensive open-source radio platform that typically allows ranges of better than 300 meters with a whip antenna kit. The range can be extended to several kilometers with the use of a directional antenna on the ground. This radio is plug-and-play with all Pixhawk Standard and other flight controllers, providing the easiest way to set up a telemetry connection between your autopilot and a ground control station. It uses open-source firmware specially designed to work well with MAVLink packets and to integrate with Mission Planner, Ardupilot, QGroundControl, and PX4 Autopilot.

The TFSIK01 is a state-of-the-art SiK-based UAV telemetry modem that incorporates dual antenna diversity and exceptional resistance to noise. This open-source hardware solution employs the advanced Si1060 chip from the Si10xx series and is further enhanced by the Si4463 EZRadioPRO transceiver, ensuring robust and secure communication capabilities. The modem's design prioritizes immunity to interference from out-of-band frequencies, guaranteeing reliable performance in challenging environments and securing its position as a top choice for UAV systems that demand the utmost data integrity and security.

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
- **High-Performance Metrics**:
  - Offers a transparent serial link
  - Facilitates air data rates reaching up to 250kbps
  - Integrates MAVLink protocol framing and status reporting
  - Achieves several kilometers of range with a small whip antenna
- **Open-Source and Highly Configurable**: Loaded with SiK firmware for enhanced customization through AT and RT commands, it supports the MAVLink 2 protocol, Configurable through Mission Planner & APM Planner


## Technical Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| Frequency range | 142 MHz - 1050 MHz | The Exact frequency band has to be set by the factory, actually available bands are 433MHz and 868 MHz|
| RF power range | -20dBm to 20dBm (100 mW) | Adjustable by AT commands |
| Input Noise Figure | 0.6 dB |  LNA noise figure |
| OIP3 |  39.5dBm | Input LNA gain 18.7dB|
| Receiver sensitivity|  -117 dBm or better | Depends on datalink bandwidth configuration |
| Bandwidth |  < 4 MHz | RF filter selective |
| RF connectors| [MCX](https://en.wikipedia.org/wiki/MCX_connector) on both RF ports | snap-on function prevents damage of connector by extensive external forces|
| Serial interface| 3.3 V UART | 6-position JST-GH connector with [handshake available](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter) |
| Operating and storage temperature | −20°C to +40°C | Limited by case material |
| Operational power voltage | +5V to +5.4V, 500mA max | Undervoltage is not treated. Current consumption is defined mainly by set RF power, Receive current is 25 mA|
| Mass | 18g | Including the housing |
| Dimensions | 55x10x35mm | Housing dimensions |
| Weather resistance | [IP40](https://en.wikipedia.org/wiki/IP_Code) | External connectors fully occupied |

### LEDs Indicators Status 

The radios have 3 status LEDs, red, orange, and green

- Green LED blinking - searching for another radio
- Green LED solid - link is established with another radio
- Red LED flashing - transmitting data
- Red LED solid - in firmware update mode
- orange solid or dimm indicates selected antenna port 

### Applications

The TFSIK01A is designed precisely for UAV command and control applications, ensuring dependable, long-distance communication links between UAVs and ground control stations. It is also highly effective in ROS2 environments for robotics, providing a reliable long-range wireless datalink.

### Installation and Configuration

Integration into UAV systems is straightforward, requiring only a Pixhawk-compatible JST-GH UART connection. The strategic placement of external antennas, connected through MCX connectors, is crucial for maximum performance efficiency.

#### Connecting to Autopilot

Connection to the autopilot is facilitated through a JST-GH cable with a 6-pin connector. While PX4 systems initially configure the TELEM1 port for telemetry connections, adjustments in the PX4 firmware settings allow for modem connections through any available UART port.

#### Ground Station Connectivity

##### Direct UART Connection

The TFSIK01 modem directly interfaces with ground stations via its UART port, enabling easy integration with Raspberry Pi or similar single-board computers equipped with 3.3V UART outputs. This direct connection method is ideal for configurations demanding low latency and direct data control.

##### USB Connectivity

To connect the modem to a computer, a USB to UART conversion is essential. The TFUSBSERIAL01 module, specifically designed for this purpose, features an FTDI VCP circuit for reliable data transmission and includes a USB-C connector for easy linking to computers or mobile devices, alongside a UART JST-GH connector for straightforward connection to the TFSIK01 modem.

This versatile setup ensures the modem's applicability across a wide range of operational scenarios, from desktop-based ground control systems to mobile field deployments.

### Purchasing Information

The device can be purchased from [ThunderFly s.r.o.](https://www.thunderfly.cz/). Contact us by email at info@thunderfly.cz for a commercial quotation. We are designers of this modem and therefore have full control of the modem construction and design. This gives us the ability to react even on non-standard requests for modification or functions.

### Frequency Options

ThunderFly typically configures the TFSIK01A modem for the 433 MHz band. For alternative frequency operations, ThunderFly can customize the modem to meet specific requirements. For detailed information on frequency adjustments, contact ThunderFly directly at [info@thunderfly.cz](mailto:info@thunderfly.cz).

{: .important }
Always verify the modem's compliance with local regulations and laws concerning frequency of operation before use. Confirm the necessity for any operational permissions or licenses within your jurisdiction.


## FAQ

### How can I connect it to a PC/mobile/tablet?

The easiest solution is the use of [TFUSBSERIAL01 gadget](https://github.com/ThunderFly-aerospace/TFUSBSERIAL01) to create a virtual UART/Serial link from a USB-A or USB-C connector.
