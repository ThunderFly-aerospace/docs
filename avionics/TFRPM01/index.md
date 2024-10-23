---
layout: page
title: "TFRPM01: RPM sensor"
permalink: /avionics/TFRPM01/
parent: Avionics
nav_order: "0"
has_children: true
---

# TFRPM01D - RPM measuring device

Revolutions per minute measurement device for UAV.
It is designed to direct connection to the Pixhawk controller (CUAV V5+ for example) through a standard I²C connector. The device [is supported by PX4 firmware](https://docs.px4.io/main/en/sensor/thunderfly_tachometer.html).
The input of the meter is supposed to be a pulse signal from an optical encoder, hall sensor, etc. The pulses are counted during a predefined constant interval.
The hardware is intended for measuring helicopter and autogyro rotor RPM, but its counting capability is up to 20 kHz, so it should also be used for measuring propeller or engine RPM.

<p align="center">
  <img src="/avionics/TFRPM01/TFRPM01D.jpg" />
</p>

## Where to get it?

ThunderFly RPM counter is commercially available from [ThunderFly s.r.o.](https://www.thunderfly.cz/), write an email to info@thunderfly.cz or shop at [Tindie store](https://www.tindie.com/products/thunderfly/tfrpm01-drone-rpm-tachometer-sensor/).

## Main Features

  * [Schmitt trigger input](https://en.wikipedia.org/wiki/Schmitt_trigger) to shape a non-uniform signal from the RPM sensing element. 
  * Offload the flight controller's MCU, by self-counting and storing the number of counted pulses in I²C accessible internal memory
  * Input status LED indicator - for easy debugging of mechanical configuration
  * Short circuit protection on the probe connector
  * Pass-trough I²C connectors to allow a daisy chain of additional or multiple sensors
  * Highly robust and repairable design. 

## Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| Pulse frequency range | 0 - 20 kHz (equal high and low periods) | Maximum RPM value varies by pulse number per revolution |
| I2C Connector | 2x 4-pin JST-GH | Connected in parallel |
| Pulse input connector | 3-pin 2.54mm pitch pin header | Internal 22k Ohm pull-up resistor |
| Pulse input voltage range | 0-5V | Negative voltage or overvoltage could damage the input |
| RPM pulse input switching thresholds | +VT 1.88 V, -VT 1.12 V  Typically@25°C| Hysteresis between VT+ and VT- is 0.756 V |
| I2C address | 0x50 default | By switching JP1 possible change to 0x51 |
| I2C SCL clock frequency | Max 100 kHz | Operation on 400 kHz is possible, but unreliable|
| Operating and storage temperature | −20°C to +40°C | Limited by case material |
| Operational power voltage | +3.6V to +5.4V | Overvoltage internally protected by Zener diode, Undervoltage is not treated. Current consumption is defined mainly by the used probe. |
| Mass | 4g PCB + 8g case | Printed case gcode included in docs |
| Dimensions | 23.5x42x12.5mm / 37.5x19mm | Case / PCB |
| Weather resistance | [IP40](https://en.wikipedia.org/wiki/IP_Code) | External connectors fully occupied |

<p align="center">
  <img src="/avionics/TFRPM01/TFRPM01D_pcb_bot.jpg" />
</p>

The 3Pin probe connector is powered from the I²C bus through an RC filter, limiting current and voltage spikes to the sensor probe.
Therefore the sensor is resistant to short circuits at the probe connector power.

The two I²C Pixhawk JST-GH connectors are interconnected. This feature allows easy nesting with other I²C devices to a single Pixhawks I²C port.

## Connection to the Pixhawk autopilot

The I²C interface connectors respect the [Pixhawk connector standard](https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf). The signal and color coding of the connector and supplied cable are described by following table (ThunderFly color scheme):

|Signal | Pixhawk Color | ThunderFly color |
|--------|------------------|---------------------|
| +5V    | Red | ![red](https://user-images.githubusercontent.com/5196729/102204855-ab1c3300-3eca-11eb-8083-646d633e3aef.png) Red |
| SCL  | Black |  ![yellow](https://user-images.githubusercontent.com/5196729/102204908-bc653f80-3eca-11eb-9a1d-a02ea5481c03.png) Yellow  |
| SDA  | Black |  ![green](https://user-images.githubusercontent.com/5196729/102205114-04846200-3ecb-11eb-8eb8-251c7e564707.png) Green |
| GND | Black  | ![black](https://user-images.githubusercontent.com/5196729/102204896-b8d1b880-3eca-11eb-8b73-656cac9104e4.png) Black |

The conductor colors in the cable are different from the Pixhawk standard to increase the visual distinction between multiple cables in the UAV.

### Wiring cable

To improve I2C bus reliability, the supplied cable is specifically twisted by following the scheme

- 10 turns for each pair SCL/+5V and SDA/GND per 30cm cable length
- The two pairs are turned again by 4 turns of pairs per 30cm cable length.

These special cable conductors' winding method greatly improves the signal integrity by minimizing the crosstalk between the SDA and SCL signals.

### I²C Address Configuration

By default, the TFRPM01C sensor is manufactured with a 0x50 I²C address. This address is possible to change to 0x51 by altering the JP1 solder junction. The junction connection to GND needs to be cut by knife and then soldered to the opposite side Vcc.

The default configuration of the junction corresponds to the following picture, where the center pin is connected to GND by copper trace.

![The default 0x50 address setup](/avionics/TFRPM01/JP1_address_0x50_config.png)

## Mounting options

The device is designed to be mounted with or without a plastic case. The 3D-printed case is intended to be adjustable to particular sensor mount options. The supplied variant of the 3D-printed case supports two mount options:

  * By default the case could be mounted by the screw on a flat surface (the original screw needs to be replaced by a longer one)
  * The second option is the use of [double-sided adhesive tape](https://www.3m.com/3M/en_US/vhb-tapes-us/) or [reclosable fastener](https://www.3m.com/3M/en_US/dual-lock-reclosable-fasteners-us/) stuck on the side of the TFRPM01 case.

## Sensor probe selection
The TFRPM01D can be used with multiple types of sensor probes. The most used one is a Hall effect probe.  The magnetic probe is ideal for harsh environments, where dirt, dust, and water can contact the sensed rotor. The disadvantage is that magnet mounting is required for proper sensor work.


<p float="center">
<img src="https://raw.githubusercontent.com/ThunderFly-aerospace/TFPROBE01/TFPROBE01A/doc/img/TFPROBE01A_connector.jpg" width="48%" />
<img src="https://raw.githubusercontent.com/ThunderFly-aerospace/TFPROBE01/TFPROBE01A/doc/img/TFPROBE01A_sensors.jpg" width="48%" />
</p>

For more information on the options and selection of the appropriate probe, please take a look at the [dedicated page Probe selection](probe.md).

## Software configuration

The TFRPM01 revolution counter is currently supported by PX4 firmware only. (Ardupilot pull requests are welcomed)
After proper connection of the sensor with the sensing probe to an I2C port (Except port I2C3) of PX4-based autopilot you should follow instructions to [PX4 software setup](https://docs.px4.io/main/en/sensor/thunderfly_tachometer.html#software-setup). After proper setup, you should get an uLog containing the RPM logged during the flight. Here is an example of rotor RPM captured during the flight of [TF-G2 autogyro](https://github.com/ThunderFly-aerospace/TF-G2). The graph is rendered by [flight_review](https://github.com/ThunderFly-aerospace/flight_review).

![TFRPM01 measurement of rotor RPM during the flight](/avionics/TFRPM01/rpm_graph.png)


# FAQ
Frequently asked questions are available on [separed TFRPM01 FAQ page](./faq.md). 
