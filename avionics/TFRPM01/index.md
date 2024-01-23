---
layout: page
title: "TFRPM01D: RPM sensor"
permalink: /avionics/TFRPM01
parent: Avionits
nav_order: "0"
---

# TFRPM01D - RPM Measuring Device

## Overview
The TFRPM01D is a device designed for measuring revolutions per minute (RPM) in UAVs. It connects directly to Pixhawk controllers like CUAV V5+ via a standard I²C connector and is compatible with PX4 firmware.

![](/doc/img/TFRPM01D.jpg)

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

![](doc/img/TFRPM01D_pcb_bot.jpg)

## Usage

### Where to Get It?
Available from [ThunderFly s.r.o.](https://www.thunderfly.cz/) or their [Tindie store](https://www.tindie.com/products/thunderfly/tfrpm01-drone-rpm-tachometer-sensor/).

### Connection to Pixhawk Autopilot
Follows the [Pixhawk connector standard](https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf) with specific color coding.

### I²C Address Configuration
Default address is 0x50, changeable to 0x51.

![The default 0x50 address setup](/doc/img/JP1_address_0x50_config.png)

### Mounting Options
Device can be mounted with or without a provided 3D-printed case.

![TFRPM01 PCB dimensions](doc/img/TFRPM01_PCB_dimensions.png)

### Sensor Probe Selection
Compatible with multiple probe types, including Hall effect and optical probes.

![TFRPM01B hall effect magnetic sensor](/doc/img/TFRPM01B_hall_sensor.jpg)
![TFRPM01B hall effect magnetic sensor connection](/doc/img/TFRPM01B_hall_connection.jpg)

## Software Configuration
Supported by PX4 firmware. Setup instructions available on the [PX4 documentation](https://docs.px4.io/main/en/sensor/thunderfly_tachometer.html#software-setup).

![TFRPM01 measuring rotor RPM during the flight](/doc/img/rpm_graph.png)