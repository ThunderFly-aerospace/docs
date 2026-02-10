---
layout: page
title: "TFGPS01 - UAV GNSS Navigation Module with RTK Capability"
permalink: /avionics/TFGPS01/
parent: Sensors
nav_order: "11"
---

# TFGPS01 - UAV GNSS Navigation Module with RTK Capability


<p align="center">
<img src="https://raw.githubusercontent.com/ThunderFly-aerospace/TFGPS01/refs/heads/TFGPS01B/doc/img/TFGPS_1.jpg" alt="3D printed box" width="80%" />
</p>

## Overview
The TFGPS01 is a high-end precision GNSS navigation module designed for UAV applications. It features multi-constellation reception, high noise immunity, and RTK capability, making it suitable for various drone navigation and payload synchronization tasks. The module can operate as both a standalone UART GPS and a USB GPS receiver.

## Key Features
- **Multi-GNSS Support**: GPS, GLONASS, Galileo, and BeiDou.
- **RTK Capable**: Achieves centimeter-level accuracy with an RTK-compatible module.
- **Compatibility**: Works with PX4, Ardupilot, and other common flight stacks.
- **Integrated Safety Features**: A beeper, safety LED, and an external safety switch connector are included.
- **Payload Interface**: Allows time synchronization and geo-fencing capabilities.
- **High Noise Immunity**: Optimized for RF-noisy environments with high-linearity and dynamic range LNA.
- **Daylight Visible LEDs**: Status indicators for power, GPS, RTK, and safety features.

## Availability

The TFGPS01A module is available for purchase from:
- [ThunderFly s.r.o.](https://www.thunderfly.cz/)
- [Lectronz](https://lectronz.com/products/1057) or [Tindie](https://www.tindie.com/products/21789/)
- For inquiries, contact: sale@thunderfly.cz

## Compatible GNSS Receiver Modules
The module is by default equipped with:
- **[uBlox NEO-9](https://www.u-blox.com/en/product/neo-m9n-module)** and a high-quality **[Taoglas](https://www.taoglas.com/product/cggp-35-3-a-02-gpsglonass-dual-band-patch-antenna-35353-5mm-2/)** patch antenna.
- It can also be equipped with **[uBlox NEO-8](https://www.u-blox.com/en/product/neo-m8p-series)** for RTK-capable GNSS receiver modes.

## High Noise Immunity
The ThunderFly TFGPS01 GNSS receiver is optimized for operation in RF-noisy environments using a high-linearity LNA at the RF input. This results in higher power usage and slightly lower sensitivity, which can be optimized for the specific application by adjusting R27 and R26 resistors.

## Hardware
The TFGPS01 is designed as open hardware (GPL v3), and all documentation is available in the GitHub repository.

![TFGPS01 without enclosure](https://raw.githubusercontent.com/ThunderFly-aerospace/TFGPS01/refs/heads/TFGPS01B/doc/img/TFGPS01A_top.jpg)

### PCB Layout

<p float="left">
<img src="https://raw.githubusercontent.com/ThunderFly-aerospace/TFGPS01/refs/heads/TFGPS01C/doc/gen/img/TFGPS01-top.png" width="45%" />
<img src="https://raw.githubusercontent.com/ThunderFly-aerospace/TFGPS01/refs/heads/TFGPS01C/doc/gen/img/TFGPS01-bottom.png" width="45%" />
</p>

### Enclosure

A 3D-printed protective enclosure is available and customizable in OpenSCAD.

![TFGPS01 enclosure](https://raw.githubusercontent.com/ThunderFly-aerospace/TFGPS01/refs/heads/TFGPS01C/doc/img/tfgps01_cap.png)

### Mechanical Drawing

![TFGPS01 dimensions](https://raw.githubusercontent.com/ThunderFly-aerospace/TFGPS01/refs/heads/TFGPS01C/doc/img/TFGPS01_dimensions.png)

### Connection Diagram
The **TFGPS01** module can be connected simultaneously to an **Autopilot** and **Payload**. Below is a standard setup:

![Typical connection of TFGPS01 to the autopilot and payload](https://raw.githubusercontent.com/ThunderFly-aerospace/TFGPS01/refs/heads/TFGPS01B/doc/img/TFGPS01_Payload_connection.jpg)

### Electronic Schematic
The full schematic is available as [KiCAD project in repository](https://github.com/ThunderFly-aerospace/TFGPS01) and also in [PDF preview](hw/cam/docs/TFGPS01A_schematic.pdf).

## LED Indicators

| LED Label | Description |
|------|------|
| ON  | Indicates 5V power in module |
| ARM | Safety LED from autopilot |
| GEO | Geofence status of uBlox |
| RTK | RTK status of uBlox |
| TPL | Timepulse from uBlox |

## Pinout
### GPS & Safety Connector

| Pin | Name | Description |
|----|------|------------|
| 1 | Vcc (+5V) | Power for module |
| 2 | RX | Data from Autopilot |
| 3 | TX | Data from TFGPS01A |
| 4 | I2C SCL | I2C clock from autopilot |
| 5 | I2C SDA | I2C data from autopilot |
| 6 | SAFETY_IN | Safety switch input |
| 7 | SAFETY_LED | Safety LED signal |
| 8 | VDD (+3.3V) | Power for safety features |
| 9 | BUZZER | Beeper signal |
| 10 | GND | Ground |

### I2C AUX Connector

I2C AUX is I2C1 output from the autopilot. No other device is connected to the I2C.

| Pin | Name |
|---|-----|
| 1  | +5V |
| 2  | SCL |
| 3  | SDA |
| 4  | GND |

### Safety Switch Connector

| Pin | Name | Description |
|---|-----|-------------|
| 1  | SAFETY_VCC | +3.3V (low current) |
| 2  | SAFETY_LED | Safety LED output |
| 3  | SAFETY_IN | Safety switch input |
| 4  | BUZZER | Beeper signal |
| 5  | +5V | Power supply |
| 6  | GND | Ground |

### Payload Connector


The module is equipped with a connector designed for payload connection; this feature is useful for time-sync and navigation data, time-stamping, or geofencing. This connection is extensively used with [TF-ATMON sensors](/instruments/TF-ATMON).

The connector is labeled as `Payload GPS Interface`.

| Pin | Name | Description |
|-----|------|-------------|
| 1   | TIMEPULSE | Time-pulse signal from uBlox GNSS receiver |
| 2   | EXTINT | Interrupt output from uBlox |
| 3   | GEO_STAT | GeoStat output from uBlox |
| 4   | SDA | I2C from uBlox |
| 5   | SCL | I2C from uBlox |
| 6   | RX | Rx of uBlox, parallel to the autopilot via a protective resistor |
| 7   | TX | Tx of uBlox, parallel to the autopilot via a protective resistor |
| 8   | GND | Autopilot GND |

### USB-C Connector
USB is connected directly to the uBlox module for configuration and testing.
Configuration via [u-center](https://www.u-blox.com/en/product/u-center).

## Technical Specifications

- **Dimensions**: 50x50x11mm.
- **Weight**: 31g.
- **Power Consumption**: 40mA (without beeper active).

For more detailed documentation and open-hardware design files, refer to the [GitHub repository](https://github.com/ThunderFly-aerospace/TFGPS01).

## Handling Precautions
- The TFGPS01 is a highly sensitive device; handle it with care.
- Avoid direct contact with the antenna to prevent damage from sweat acids.


