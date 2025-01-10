---
layout: page
title: "TFCO201 - Airborne CO2 concentration sensor"
permalink: /avionics/TFCO201/
parent: Sensors
nav_order: "10"
---

# TFCO201 - Airborne CO2 Concentration Sensor

The TFCO201 sensor measures carbon dioxide (CO2) concentrations in airborne applications. It supports integration with UAVs and can be used with a Pixhawk autopilot system or as a part of the TF-ATMON monitoring system.


![TFCO201 sensor](https://github.com/ThunderFly-aerospace/TFCO201/assets/5196729/bca47559-f115-4941-bb79-61ccec8639b7)

This sensor uses the SCD41 CO2 sensor for high-accuracy measurements and includes additional environmental data such as temperature and humidity.

## Features
- **CO2 measurement range**: 400 – 5000 ppm
- **Accuracy**: ±(40 ppm + 5 % of reading) for CO2
- **Humidity range**: 0% to 100% RH
- **Temperature range**: -10°C to 60°C
- **Communication Interface**: I2C with address 0x62
- **Power supply**: 3.6V to 5.4V
- **Low power consumption**: Supports low power periodic measurements
- **Compact size**: 30 x 15 x 6.5 mm (PCB only without housing)

## Applications
- **Atmospheric sounding**: Ideal for direct measurements in atmospheric research via UAVs.
- **Urban air quality monitoring**: Helps locate and map sources of CO2 emissions.
- **Ecosystem change observation**: Suitable for tracking CO2 levels in various ecosystems.
- **Industrial emission control**: Monitor CO2 emissions from industrial facilities.

## Sensor Parameters

| Parameter                    | Value                               | Notes                                       |
|------------------------------|-------------------------------------|---------------------------------------------|
| **CO2 Sensor Model**          | SCD41                              | Other supported sensors: SCD40, SCD42       |
| **CO2 Accuracy**              | ± (40 ppm + 5% of reading)          | Measurement range: 400 – 5000 ppm           |
| **Humidity Measurement Range**| 0% – 100% RH                       |                                             |
| **Temperature Accuracy**      | ± 1.5 °C                           | Temperature range: -10 °C to 60 °C          |
| **Operating Voltage**         | 3.6 – 5.4V                         | Internal overvoltage protection              |
| **Interface**                 | I2C (0x62)                         | Supports I2C address modification           |
| **Mass**                      | 3 g                                | Without cabling                             |
| **Dimensions**                | 30 x 15 x 6.5 mm                   | PCB size                                    |
| **Weather Resistance**        | IP40                               | External connectors fully occupied          |

## Usage Instructions

The sensor can be integrated directly with UAV systems. The PX4 autopilot supports it and allows real-time data logging and communication with the ground station. For extended usage scenarios and system setup, refer to the sensor’s [GitHub repository](https://github.com/ThunderFly-aerospace/TFCO201).

### Installation & Calibration
- **I2C Address Setup**: Default address is 0x62, which can be translated using the TFI2CADT01 module.
- **Temperature Offset**: The sensor supports temperature offset configuration to improve accuracy.

## Schematics
[TFCO201 Schematics](https://github.com/ThunderFly-aerospace/TFCO201/blob/TFCO201A/doc/gen/TFCO201-schematic.pdf)

## Datasheet Reference
For more detailed technical specifications of the CO2 sensor used, refer to the [Sensirion SCD41 Datasheet](https://sensirion.com/media/documents/E0F04247/631EF271/CD_DS_SCD40_SCD41_Datasheet_D1.pdf).

