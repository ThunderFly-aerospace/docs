---
layout: page
title: "TFSIK01: High-reliable wireless telemetry data link"
permalink: /avionics/TFSIK01/
parent: "Communication & Interfaces"
nav_order: "10"
---

# TFSIK01 - High-Performance Telemetry Modem


![TFSIK01 pair with USB-C converter](https://raw.githubusercontent.com/ThunderFly-aerospace/TFSIK01/TFSIK01A/doc/img/TFSIK01_pair.jpg)

### Overview

The SiK Telemetry Radio is a small, light, and inexpensive open-source radio platform that typically allows ranges of better than one kilometer with a basic whip antenna kit. The range can be extended to several kilometers with the use of a directional antenna on the ground. This radio is plug-and-play with all Pixhawk Standard and other flight controllers, providing the easiest way to set up a telemetry connection between the UAV and a ground control station. It uses open-source firmware specially designed to work well with MAVLink packets and to integrate with Mission Planner, Ardupilot, QGroundControl, and PX4 Autopilot.

The TFSIK01 is a state-of-the-art SiK-based UAV telemetry modem that incorporates dual antenna diversity and exceptional resistance to noise. This open-source hardware solution employs the advanced [Si1060](https://www.silabs.com/documents/public/data-sheets/Si106x-8x.pdf) chip from the Si10xx series and is further enhanced by the Si4463 EZRadioPRO transceiver, ensuring robust and secure communication capabilities. The modem's design prioritizes immunity to interference from out-of-band frequencies, guaranteeing reliable performance in challenging environments and securing its position as a top choice for UAV systems that demand the utmost data integrity and security.

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
- Orange LED solid or dimm indicates the selected antenna port 

### Applications

The TFSIK01A is designed precisely for UAV command and control applications, ensuring dependable, long-distance communication links between UAVs and ground control stations. It is also highly effective in ROS2 environments for robotics, providing a reliable long-range wireless datalink.

The modem was originally developed for the transmission of atmospheric data measured in real-time using the [TF-ATMON system](https://docs.thunderfly.cz/instruments/TF-ATMON).

### Installation and Configuration

Integration into UAV systems is straightforward, requiring only a [Pixhawk-compatible JST-GH UART connection](https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf). The side placement of external antennas, connected through MCX connectors, is specifically selected to increase robustness and ease of installation.

### Additional Telemetry Parameters

| Parameter | Description |
|-----------|-------------|
| **Baud** (default 57) | The rate at which the mission planner or vehicle communicates with the local radio. "57" = 57600 bits per second. Must match the serial port settings on both ends. |
| **Air Speed** (default 64) | The rate at which the two radios communicate. It is the rate in kbps, truncated to an integer. "9" = 9600 baud, "38" means 38400, "64" = 64kbps, "115" = 115200 etc. Lowering this rate increases range but reduces data throughput. |
| **ECC** (default is "0" off) | Controls whether error correction is used. When on, 12/24 Golay error correction is applied, adding a 16-bit CRC. This theoretically improves reliability but halves throughput. Has minimal benefit in the case of MAVlink framed data. |
| **MAVlink** (default is "1" (MAVLink) | Optimizes transmission for MAVLink packets. Set to 2 "Low Latency" if using a joystick or tablet control. RSSI and error rates are only sent in MAVLink mode. For general data set to "0" |
| **Tx Power** (default 20) | Transmission power in dBm. Should comply with local regulations. |
| **Duty Cycle** (default 100) | Max % of time the radio transmits. A lower duty cycle may enable higher transmit power or broader frequency access (e.g., <10% in the EU). Bandwidth decreases with lower duty cycles. A duty cycle of 0 means receive-only mode. |
| **Max Window** (default 33) | The interval (in ms) within which the GCS can send a packet. Lower values like 33 reduce latency, especially in "Low Latency" mode. |
| **LBT Rssi** (default 0) | RSSI threshold for Listen Before Talk (LBT). If >0, the radio waits for a quiet channel before transmitting. Formula: `signal_dBm = (RSSI / 1.9) - 127`. Example: 25 = -121 dBm. Required for compliance in some regions. Minimum listen time is 5ms, with randomized delay per EU rules. |
| **RTS CTS** | Enables RTS/CTS hardware flow control. Useful with ArduPilot firmware (post mid-2016) when connected to Pixhawk TELEM ports. Can be set to "auto" to optimize performance. |

#### Connecting to Autopilot

Connection to the autopilot flight controller is facilitated through a JST-GH cable with a 6-pin connector. While PX4 firmware initially configures the TELEM1 port for telemetry connections, adjustments in the PX4 or Ardupilot firmware settings allow for modem connections through any available UART port. 

#### Ground Station Connectivity

##### Direct UART Connection

The TFSIK01 modem directly interfaces with ground stations via its UART port, enabling easy integration with Raspberry Pi or similar single-board computers equipped with 3.3V UART outputs. This direct connection method is ideal for configurations demanding low latency and direct data control.

##### USB Connectivity

To connect the modem to a computer, a USB to UART conversion is essential. The [TFUSBSERIAL01 module](https://docs.thunderfly.cz/avionics/TFUSBSERIAL01/), specifically designed for this purpose, features an FTDI-based USB chip for reliable data transmission and includes a USB-C connector for easy linking to computers or mobile devices, alongside a UART JST-GH connector for straightforward connection to the TFSIK01 modem.

This versatile setup ensures the modem's applicability across a wide range of operational scenarios, from desktop-based ground control systems to mobile field deployments.

### Purchasing Information

The device can be purchased from [ThunderFly s.r.o.](https://www.thunderfly.cz/). Contact us by email at sale@thunderfly.cz for a commercial quotation or shop directly in [Tindie store](https://www.tindie.com/products/34682/). We are designers of this modem and therefore have full control of the modem construction and design. This gives us the ability to react even on non-standard requests for modification or functions.

### Frequency Options

ThunderFly typically configures the TFSIK01A modem for the 433 MHz band. For alternative frequency operations, ThunderFly can customize the modem to meet specific requirements. For detailed information on frequency adjustments, contact ThunderFly directly at [info@thunderfly.cz](mailto:info@thunderfly.cz).

{: .important }
Always verify the modem's compliance with local regulations and laws concerning frequency and transmitting power for operation before use. Confirm the necessity for any operational permissions or licenses within your jurisdiction.


## FAQ

### How can I connect it to a PC/mobile/tablet?

The easiest solution is the use of [TFUSBSERIAL01 gadget](https://docs.thunderfly.cz/avionics/TFUSBSERIAL01/) to create a virtual UART/Serial link from a USB-A or USB-C connector.


### How I can update the firmware?

Download the latest [firmware release](https://github.com/ThunderFly-aerospace/SiK/releases) and flash it to the TFSIK01 by using the following command:

    python3 uploader.py --port /dev/ttyUSB0 radio~tfsik01a.ihx 


### How can I monitor the link quality?

The SiK modem firmware provides telemetry signal strength data (RSSI) that can be visualized in Ground Control Station software such as Mission Planner or QGroundControl. Two RSSI values are reported:

  * Local RSSI: signal strength received by the local modem.
  * Remote RSSI: signal strength received by the remote modem.
  * Local Noise: The noise floor being received in the aircraft.
  * Remote Noise: The nooise level being received on the ground.


Monitoring both values provides insight into the quality and symmetry of the communication link as is demonstrated in the following graph. As seen in the figure, the signal strength for TFSIK01 decreases almost smoothly with increasing distance, making it easier to predict link performance and diagnose issues caused by interference or configuration problems.

![TFSIK01 PX4 RSSI recording during flight](./TFSIK01_RSSI_distance.png)

Thanks to dual antenna diversity system, the TFSIK01 maintains stable signal levels even when the UAV changes orientation. Unlike conventional modems where antenna directionality causes fluctuations, the TFSIK01  switches between two antennas to maintain the best signal. The used [PlotJuggler](https://plotjuggler.io/) layout [could be downloaded here](./Plot_juggler_RSSI.xml).

A reliable telemetry link depends not only on received signal strength (RSSI), but also on the link signal-to-noise ratio (SNR), because the link could be degraded due to background noise.
This is because the effective **SNR** (RSSI – Noise) becomes too small for reliable demodulation and  basically if the RSSI and background noise level (Noise) meets in the graph, the radio link is lost.

The recommended minimum SNR for a reliable MAVLink connection is approximately 10 dB. If the noise level increases (due to interference or hardware issues), the same RSSI may no longer be sufficient.

The figure above shows both RSSI and Noise values from both ends of the link. If you encounter packet loss or poor range despite good RSSI values, examine the corresponding noise measurements.

If SNR is consistently insufficient, consider:

  - **Reducing interference**: improve RF shielding and move away modem and antenna from EMI emitting  devices such, power supplies, or switching regulators.
  - **Lowering the air data rate**: slower rates improve link robustness and increase receiver sensitivity.
  - **Using directional antennas** (especially on ground side) to improve gain and reject side noise.




