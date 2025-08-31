---

title: "TF-ATMON - Toolchain for Atmospheric measurement"
layout: page
permalink: /instruments/TF-ATMON
parent: Instruments
nav_order: "4"
---

# TF-ATMON - Toolchain for Atmospheric measurement by drones

ThunderFly TF-ATMON is a complete system for performing in-situ atmospheric measurements. It provides a universal tool for increasing the effectiveness of scientific measurements, simplifying pre-flight preparations, and improving the quality of collected data. The system combines an aerial platform carrying specialized sensors (for humidity, gases, airborne particles, ionizing radiation, electric fields, etc.) with a ground station for real-time data visualization and flight planning.

The ground station not only allows operators to monitor data live, but also supports smart trajectory optimization based on measured values. This reduces the need for pilot interventions and ensures measurements are conducted efficiently and with higher spatial resolution. Thanks to its modular design, TF-ATMON can be integrated with different types of unmanned platforms — from autogyros and multicopters to fixed-wing aircraft or even stratospheric balloons — depending on mission requirements.

### System features

* **Measured quantities:** temperature, humidity, airborne particles (PM0.5–PM10), ionizing radiation, gases (CO2, O3, SOx, NOx…), electric field intensity. Additional sensor types can be integrated on request.
* **Ground control station:** provides real-time visualization, operator terminal, and a smart trajectory optimization algorithm.
* **Planning algorithm:** decreases dependency on the pilot and ensures measurements are performed optimally with respect to quality and duration.
* **System infrastructure:** TF-ATMON is built on existing multi-vendor UAV avionics and communication infrastructure, using a telemetry link and the [MAVlink transmission protocol](https://en.wikipedia.org/wiki/MAVLink) for reliable data exchange between the aerial platform and ground station.

See the following video for a demonstration flight of a particulate matter sensor mounted on [TF-G2 autogyro](/instruments/TF-G2) and looking for a smoke atmospheric pollution source.

[![TF-ATMON particulate matter sensing demonstration](https://img.youtube.com/vi/KUhktPDEi8I/hqdefault.jpg)](https://www.youtube.com/watch?v=KUhktPDEi8I)

## Vendor information

ThunderFly TF-ATMON is commercially available as a service from [ThunderFly s.r.o.](https://www.thunderfly.cz/). Write an email to [info@thunderfly.cz](mailto:info@thunderfly.cz) to request more details.

## TF-ATMON compatible sensors

The following table summarises existing (in production) sensor devices. Other sensors are under testing.

| Device identification                                     | Data type | Description                                                              |
| --------------------------------------------------------- | --------- | ------------------------------------------------------------------------ |
| [TFPM01](/avionics/TFPM01) and [TFPM02](/avionics/TFPM02) | 1         | Particulate matter sensors                                               |
| [TFHT01](/avionics/TFHT01) and [TFHT02](/avionics/TFHT02) | 2         | Humidity and temperature sensors                                         |
| [THUNDERMILL01](/avionics/THUNDERMILL01)                  | 3         | Electric field sensors                                                   |
| [AIRDOS03 ("UAVDOS")](/avionics/AIRDOS03/)                | 4         | Semiconductor-based ionising radiation spectrometers designed for drones |
| [TFCO201](/avionics/TFCO201)                              | 5         | Opto-aucoustic CO2 concentration sensor                                  |

Additional sensors could be connected by using the [TFUNIPAYLOAD01](/avionics/TFUNIPAYLOAD01) hardware, which slightly increases the weight, but does not require the development of a PX4/Ardupilot-specific sensor driver.

## Supported airframes

TF-ATMON has been successfully integrated into various aerial platforms for atmospheric measurement:

* **Autogyros**

  * [TF-G250](/instruments/TF-G250) – Ultra-compact aerological autogyro platform for atmospheric sounding
  * [TF-G2](/instruments/TF-G2) – larger, more robust autogyro platform suitable for advanced sensor integration and research flights
* **Multicopters** – Customer specific integrations
* **Stratospheric balloons**
  
  * [TF-B1](/instruments/TF-B1) – high-altitude experimental balloon platform
* **Fixed-wing aircraft** – supported for long-endurance atmospheric missions (customer-specific integrations)

These supported airframes allow TF-ATMON to cover a wide range of atmospheric measurement and research applications.

## Simulation support

The entire TF-ATMON system is also compatible with the [TF-Simulator](/instruments/TF-simulator), enabling testing and development in virtual environments without the need for physical flights.

## Scientific papers

  * [MEASUREMENT OF THE REGENER-PFOTZER MAXIMUM USING DIFFERENT TYPES OF IONISING RADIATION DETECTORS AND A NEW TELEMETRY SYSTEM TF-ATMON ](https://pubmed.ncbi.nlm.nih.gov/36005953/)
  

