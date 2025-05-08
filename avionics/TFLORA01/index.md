---
layout: page
title: "TFLORA01: LoRa and FSK Transceiver"
permalink: /avionics/TFLORA01/
parent: "Communication & Interfaces"
nav_order: "0"
has_children: false
---

# TFLORA01 - UAV LoRa and FSK Transceiver

The TFLORA01 device is designed for long-range telemetry transmission from UAVs using LoRa technology. It operates in the sub-GHz frequency band and is based on the Semtech SX1262 transceiver, which supports LoRa and (G)FSK modulation for various telemetry and IoT applications.

![TFLORA01 Top](TFLORA01-top.png)

![TFLORA01 Bottom](TFLORA01-bottom.png)

This module does not contain any onboard firmware, providing greater flexibility for custom implementations. Firmware for communication protocols such as MAVLink is provided by out-of-tree driver in the PX4 autopilot system. The absence of firmware in the transceiver module allows for enhanced versatility, such as the ability to send standard MAVLink telemetry streams while occasionally transmitting LoRa packets to a LoRaWAN IoT network.

For detailed usage instructions or custom integration, please contact **[ThunderFly](https://www.thunderfly.cz/contact-us.html)**.

## Features

- **Chipset**: SX1262 RF transceiver
  - Supports LoRa modulation for low-power, long-range communication
  - Transmits up to +22 dBm with a highly efficient integrated power amplifier
- **Frequency Bands**: 150 MHz to 960 MHz (supports global ISM bands)
- **Protocols Supported**:
  - LoRaWAN™ connection to IoT networks like [The Things Network](https://www.thethingsnetwork.org/)
  - Custom proprietary protocols
  - SiK MAVLink transmissions
- **UAV Telemetry**: Integrated with PX4 autopilot firmware for MAVLink communication
- **IoT Integration**: Capable of sending LoRaWAN packets to IoT networks

## Technical Specifications

| Parameter      | Value                | Description                         |
|----------------|----------------------|-------------------------------------|
| Dimensions     | 55 x 30 mm           | PCB size                            |
| Output Power   | Up to +22 dBm        | RF output power (SX1262)            |
| Frequency Range| 150 MHz - 960 MHz    | Supports all major sub-GHz ISM bands like 433 and 868 MHz   | 
| Antenna connector | [MCX RF](https://en.wikipedia.org/wiki/MCX_connector)            |  Connection of an external passive antenna is expected      | 
| FC Interface   | 7-PIN JST-GH SPI     | [Pixhawk SPI connector defined by standard](https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf)|
| Power Supply   | 3.7-5.4V@100mA       | Suitable for miniature UAVs   |

## Usage

The module is intended to be connected by SPI to the flight controller (FC), with the FC's firmware handling MAVLink telemetry streams. The custom-formatted packets can be transmitted in multiple different formats and protocols, enhancing UAV-to-ground network capabilities. This multi-modulation use case is ideal for integrating UAV operations with broader infrastructure.

### LoRaWAN

Currently, support for connection to LoRaWAN networks is implemented in PX4. This allows the device to transmit telemetry or other data to IoT services such as The Things Network. This use case is intended to secure reliable mission-critical telemetry downloads from UAVs. The control of UAVs is very limited to a  few commands.

### TheTingsNetwork

The following example demonstrates how to transmit position packets to [The Things Network](https://www.thethingsnetwork.org/).

To enable position transmission using TFLORA, the PX4 firmware must be compiled with the following configuration options:

```bash
CONFIG_DRIVERS_TFLORA=y
CONFIG_MODULES_LORA_GPS_VCMD=y
```

For testing purposes, you may also enable the fake GPS data generator:

```bash
CONFIG_EXAMPLES_FAKE_GPS=y
```

After flashing the appropriate PX4 firmware, create a file named `tflora.txt` The following is an anonymous example of tflora.txt in the root of the SD card with your TTN connection credentials. You should modify it by using your keys:

```
n:5D5A273AD1F54F2503A8FF99796E3DC9
a:03 CF 72 CE 1A 38 13 63 6B C4 44 CC 3B 04 6D CE
d:36 02 15 83
```

To connect to a PixHawk-compatible FMC, use the 7-wire SPI cable. The firmware is configured so that the second chip select (CS) line functions as the DRDY (data ready) signal.

The implementation consists of two parts:

* **tflora**: A driver that includes a modified LMIC library. It controls the hardware and communicates with PX4 via the uOrb topics:

  * `lora_outgoing_message` (PX4 → TTN)
  * `lora_incoming_message` (TTN → PX4)

Messages are transmitted immediately upon reception. Start the module with:

```bash
tflora -S start
```

This selects the first external SPI bus, typically suitable for`fmu-v5` on `cuav-v5+` boards.

Example terminal output:

```bash
NuttShell (NSH) NuttX-11.0.0
nsh> tflora -S start
tflora #0 on SPI bus 6 (external, equal to '-b 1')
nsh>
```

Relevant log output (from `dmesg`):

```text
INFO  [tflora] drdy: 315
INFO  [tflora] TFLORA Probe!
INFO  [tflora] I see the tflora!
app: 6d 3c 26 9a d2 f5 2f 25 02 a8 fa 95 79 6e 3e c9
net: 02 cd 73 de 2a 38 14 62 3b c4 44 cc 3b 04 6d cf
dev: 637504895 26 02 33 83
INFO  [tflora] init_lmic
Off to the loop!
```

To simulate GPS data:

```bash
fake_gps start
```

To transmit GPS positions periodically (every 30 seconds), use the module:

```bash
lora_gps_vcmd start
```

Note: At this stage, `lora_gps_vcmd` does not yet process TTN → PX4 messages and only prints them.

Example transmission log entries:

```text
INFO  [tflora] received lora message for send
INFO  [tflora] sending lora message...
EV_TXSTART
EV_TXCOMPLETE (includes waiting for RX windows)
```

You should observe the most recent activity in the TTN console within a few seconds (top-right corner).

### Command and Control (C2) Links

The bidirectional telemetry and command transmission links enable real-time telemetry and simultaneous control of UAVs.

#### mLRS
The next step on the development roadmap is the implementation of support for [mLRS](https://github.com/olliw42/mLRS). This system enables flexible and long-range telemetry communication beyond conventional LoRaWAN capabilities and offers combined RC-like control.

### SiK
Another planned feature is the implementation of a driver to enable compatibility with the [SiK firmware](https://github.com/ThunderFly-aerospace/SiK) and packet format. This would allow the TFLORA01 module to integrate with existing radio communication setups using the SiK protocol.

## Integration with PX4

The TFLORA01 module is compatible with PX4, which manages the primary MAVLink telemetry transmissions. As the module does not include any pre-programmed firmware, users have the flexibility to implement additional features, such as periodic LoRaWAN packet transmission alongside standard telemetry streams.


