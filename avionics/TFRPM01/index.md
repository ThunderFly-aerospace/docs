---
layout: page
title: "TFRPM01: RPM sensor"
permalink: /avionics/TFRPM01
parent: Avionics
nav_order: "0"
---

# TFRPM01 - RPM Measuring Sensor

<p align="center">
  <img src="/avionics/TFRPM01/TFRPM01D.jpg" />
</p>

## Overview
The TFRPM is a device designed for measuring revolutions per minute (RPM) in UAVs. It connects directly to Pixhawk controllers like CUAV V5+ via a standard I²C connector and is compatible with PX4 firmware.

## Specifications

### Features
- **Schmitt Trigger Input**: To shape non-uniform signals from RPM sensing elements.
- **Self-Counting and Memory**: Offloads the flight controller's MCU.
- **LED Indicator**: For input status, optionally visible in daylight.
- **Protection**: Short circuit protection on the probe connector.
- **I²C Connectors**: Pass-through connectors for daisy-chaining sensors.
- **Design**: Robust and repairable.

### Technical Parameters
- **Pulse Frequency Range**: 0 - 20 kHz.
- **I2C Connector**: 2x 4-pin JST-GH.
- **RPM Connector**: 3-pin 2.54mm pitch header.
- **I2C Address**: 0x50 default, alterable to 0x51.
- **Operating Temperature**: −20°C to +40°C.
- **Input Voltage**: +3.6V to +5.4V.
- **Mass**: 12g (4g PCB + 8g case).
- **Dimensions**: Case - 23.5x42x12.5mm, PCB - 37.5x19mm.
- **Weather Resistance**: IP40.

<p align="center">
  <img src="/avionics/TFRPM01/TFRPM01D_pcb_bot.jpg" />
</p>


<a href="https://www.tindie.com/products/thunderfly/tfrpm01-drone-rpm-tachometer-sensor/"><img src="https://d2ss6ovg47m0r5.cloudfront.net/badges/tindie-mediums.png" alt="I sell on Tindie" width="200" align="right"></a>
### Where to Get It?

Available from [ThunderFly s.r.o.](https://www.thunderfly.cz/) or their [Tindie store](https://www.tindie.com/products/thunderfly/tfrpm01-drone-rpm-tachometer-sensor/).

### Connection to Pixhawk Autopilot
Follows the [Pixhawk connector standard](https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf) with specific color coding.

### I²C Address Configuration
Default address is 0x50, changeable to 0x51.

![The default 0x50 address setup](/avionics/TFRPM01/JP1_address_0x50_config.png)

### Mounting Options
Device can be mounted with or without a provided 3D-printed case.

![TFRPM01 PCB dimensions](avionics/TFRPM01/TFRPM01_PCB_dimensions.png)

### Sensor Probe Selection
Compatible with multiple probe types, including Hall effect and optical probes.

![TFRPM01B hall effect magnetic sensor](/avionics/TFRPM01/TFRPM01B_hall_sensor.jpg)
![TFRPM01B hall effect magnetic sensor connection](/avionics/TFRPM01/TFRPM01B_hall_connection.jpg)

## Software Configuration
Supported by PX4 firmware. Setup instructions available on the [PX4 documentation](https://docs.px4.io/main/en/sensor/thunderfly_tachometer.html#software-setup).

![TFRPM01 measuring rotor RPM during the flight](/avionics/TFRPM01/rpm_graph.png)
