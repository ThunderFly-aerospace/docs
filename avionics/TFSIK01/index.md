---
layout: page
title: "TFSIK01: High-reliable wireless data link"
permalink: /avionics/TFSIK01/
parent: Avionics
nav_order: "10"
---

# TFSIK01 Telemetry Modem

### Overview

The TFSIK01 is a state-of-the-art UAV telemetry modem that incorporates dual antenna diversity and exceptional resistance to noise. This open-source hardware solution employs the advanced Si1060 chip from the Si10xx series and is further enhanced by the Si4463 EZRadioPRO transceiver, ensuring robust and secure communication capabilities. The modem's design prioritizes immunity to interference from out-of-band frequencies, guaranteeing reliable performance in challenging environments and securing its position as a top choice for UAV systems that demand utmost data integrity and security.

### Key Features

- **Superior Noise Immunity**: With a hardware-optimized RF front-end, the modem excels in environments plagued by out-of-band signal interference.
- **Robust Hardware Design**: Housed in a customizable 3D printed enclosure with electromagnetic shielding, it promises both durability and adaptability.
- **Antenna Diversity**: Employs dual external antennas via MCX connectors, enhancing connectivity flexibility across different frequency bands, with a primary focus on the 433 MHz band for optimal performance.
- **Cutting-Edge Communication Technologies**:
  - Implements Frequency-Hopping Spread Spectrum (FHSS)
  - Utilizes Adaptive Time Division Multiplexing (TDM)
  - Supports Listen Before Talk (LBT) and Adaptive Frequency Agility (AFA)
- **High-Performance Metrics**:
  - Offers a transparent serial link
  - Facilitates air data rates reaching up to 250kbps
  - Integrates MAVLink protocol framing and status reporting
  - Achieves several kilometers of range with a small whip antenna
- **Open-Source and Highly Configurable**: Loaded with SiK firmware for enhanced customization through AT and RT commands, it supports the MAVLink 2 protocol and is compatible with multiple frequency bands.

### Applications

The TFSIK01A is designed with precision for UAV command and control applications, ensuring dependable, long-distance communication links between UAVs and ground control stations. It is also highly effective in ROS2 environments for robotics, providing a reliable long-range wireless datalink.

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

:::note
Always verify the modem's compliance with local regulations and laws concerning frequency operation before use. Confirm the necessity for any operational permissions or licenses within your jurisdiction.
:::



## FAQ

### How can I connect it to a PC/mobile/tablet?

The easiest solution is the use of [TFUSBSERIAL01 gadget](https://github.com/ThunderFly-aerospace/TFUSBSERIAL01) to create a virtual UART/Serial link from a USB-A or USB-C connector.
