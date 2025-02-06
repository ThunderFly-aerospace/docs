---
layout: page
title: "TFHT02 - Fast response UAV Humidity and Temperature Sensor"
permalink: /avionics/TFHT02/
parent: Sensors
nav_order: "20"
---

# TFHT02 - Fast response miniature UAV Humidity and Temperature Sensor

The TFHT02 is a compact and precise hygrometer and temperature sensor designed for atmospheric measurements by UAVs. It offers flexible integration options and can be directly connected to a Pixhawk based autopilot with PX4 firmware and used as a sensor for the [TF-ATMON monitoring system](https://www.thunderfly.cz/tf-atmon.html). The **fast response time** and **reduced sensitivity to solar radiation** make it ideal for meteorological measurements, particularly in atmospheric profiling applications.

![TFHT02A atmospheric profiling](https://raw.githubusercontent.com/ThunderFly-aerospace/TFHT02/refs/heads/TFHT02A/doc/img/TFHT_vertical_profile_measurement.png)

## Features
- **Designed for UAVs**: Lightweight and compact construction
- **Fast Response**: Optimized for real-time environmental changes
- **Broad Compatibility**: Supports PX4 autopilot firmware
- **High Accuracy and repeatability**: ±1% RH and ±0.1°C
- **Robust Design**: Reduced sensitivity to solar radiation
- **Flexible Integration**: Can be used with TF-ATMON and Pixhawk.

## Where to Buy?
The TFHT02 is available from [ThunderFly s.r.o.](https://www.thunderfly.cz/). 

For a quotation or support, contact us at sale@thunderfly.cz or visit our [Tindie store](https://www.tindie.com/stores/thunderfly/).

## Technical Specifications

| Parameter | Value | Description |
|-----------|-------|-------------|
| **Sensing element** | [SHT45](https://sensirion.com/media/documents/213E6A3B/63A5A569/Datasheet_SHT3x_DIS.pdf) | Alternatives: SHT40 or SHT41 |
| **Typical accuracy** | ±1 %RH, ±0.1 °C | |
| **Repeatability** | ±0.15 %RH, ±0.08 °C | 3σ of consecutive measurements at constant conditions |
| **Operating temperature range** | 0 °C to +65 °C | Sensor measures from -40°C to +120°C with reduced accuracy |
| **Operating humidity range** | 0-100 % | Accuracy degrades above 80% for prolonged periods |
| **I2C Connector** | 4-pin JST-GH | Optional second connector on the opposite side |
| **I2C Address** | 0x44 | |
| **Storage temperature** | -20 °C to +40 °C | |
| **Input voltage** | 3.6 - 5.4V | Overvoltage protected by Zener diode |
| **Mass** | 2 g | PCB without cables |
| **Dimensions** | 30 × 15 × 6.5 mm | PCB size |
| **Weather resistance** | IP40 | When all external connectors are occupied |

## Design and Functionality

The TFHT02 sensor is built for fast response and minimal sensitivity to solar radiation. The sensing element has low thermal mass, allowing rapid adaptation to environmental changes. It is designed to maximize airflow exposure, ensuring accurate and efficient real-time meteorological measurements.

![TFHT02A top view](https://raw.githubusercontent.com/ThunderFly-aerospace/TFHT02/refs/heads/TFHT02A/doc/gen/img/TFHT02-top.png)
![TFHT02A bottom view](https://raw.githubusercontent.com/ThunderFly-aerospace/TFHT02/refs/heads/TFHT02A/doc/gen/img/TFHT02-bottom.png)

### Electrical Schematics

[![Schematics](https://raw.githubusercontent.com/ThunderFly-aerospace/TFHT02/4c2eb72befc698d74adc7a1e7da0c1ca51e37155/doc/gen/TFHT02-schematic.svg)](https://github.com/ThunderFly-aerospace/TFHT02/blob/TFHT02A/doc/gen/TFHT02-schematic.pdf)

## PX4 Autopilot Integration

The PX4 firmware supports TFHT02 out of the box. Multiple sensors can be connected to a single autopilot. The measured data could be sent to the ground station and logged in the onboard ulog file.

To enable support, set [SENS_EN_SHT4X](http://docs.px4.io/master/en/advanced_config/parameter_reference.html#SENS_EN_SHT3X) = 1.

### Command Line Usage (CLI)
Start the sensor driver on the external I2C bus:
```sh
sht4x start -X
```

Check driver status:
```sh
sht4x status
```

Print last measured values:
```sh
sht4x values
```

Reinitialize the sensor:
```sh
sht4x reset
```

### Full PX4 Driver Command Reference
```sh
sht4x <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  Board-specific bus (default=all)
     [-f <val>]  Bus frequency in kHz
     [-q]        Quiet startup (no message if no device found)
     [-a <val>]  I2C address (default: 68)
     [-k]        Retry initialization periodically if probing fails

   stop          Stop driver
   status        Print driver status
   values        Print sensor data
   reset         Reinitialize sensor
```

## Ardupilot Support

Currently, Ardupilot does not support the TFHT02 sensor as the sht4x driver is missing. Contributions to add support are welcome.

