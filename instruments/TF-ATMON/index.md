---
title: "TF-ATMON - Toolchain for Atmospheric measurement"
layout: page
permalink: /instruments/TF-ATMON
parent: Instruments
nav_order: "4"
---

# TF-ATMON - Toolchain for Atmospheric measurement by drones

Public part of the TF-ATMON tool product. In case you need more details, please contact [ThunderFly s.r.o.](https://www.thunderfly.cz/) with a request. Generic information you could find in the [TF-ATMON fact sheet](https://www.thunderfly.cz/tf-atmon/ThunderFly_TFATMON_factsheet_en.pdf)

See the following video for a demonstration flight of a particulate matter sensor mounted on [TF-G2 autogyro](/instruments/TF-G2) and looking for a smoke atmospheric pollution source.

[![TF-ATMON particulate matter sensing demonstration](https://img.youtube.com/vi/KUhktPDEi8I/hqdefault.jpg)](https://www.youtube.com/watch?v=KUhktPDEi8I)

## Vendor information

ThunderFly TF-ATMON is commercially available as a service from [ThunderFly s.r.o.](https://www.thunderfly.cz/). Write an email to info@thunderfly.cz to request more details.


## TF-ATMON compatible devices

The following table summarises existing (in production) sensor devices. Other sensors are under testing.

| Device identification | Data type | Description |
|----------------|---------|-------|
| [TFPM01](/avionics/TFPM01) and [TFPM02](/avionics/TFPM02) | 1 | Particulate matter sensors |
| [TFHT01](/avionics/TFHT01) and [TFHT02](/avionics/TFHT02) | 2 | Humidity and temperature sensors |
| [THUNDERMILL01](/avionics/THUNDERMILL01) | 3 | Electric field sensors |
| [AIRDOS03 ("UAVDOS")](/avionics/AIRDOS03/) | 4 | Semiconductor-based ionising radiation spectrometers designed for drones |
| [TFCO201](/avionics/TFCO201)| 5 | Opto-aucoustic CO2 concentration sensor |

Additional sensors could be connected by using the [TFUNIPAYLOAD01](/avionics/TFUNIPAYLOAD01) hardware, which slightly increases the weight, but does not require the development of a PX4/Ardupilot-specific sensor driver.

## Scientific papers

  * [MEASUREMENT OF THE REGENER-PFOTZER MAXIMUM USING DIFFERENT TYPES OF IONISING RADIATION DETECTORS AND A NEW TELEMETRY SYSTEM TF-ATMON ](https://pubmed.ncbi.nlm.nih.gov/36005953/)
