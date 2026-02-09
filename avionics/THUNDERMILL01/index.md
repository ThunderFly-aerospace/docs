---
layout: page
title: "THUNDERMILL01: Airborne E-field sensor"
permalink: /avionics/THUNDERMILL01/
parent: "Sensors"
nav_order: "99"
has_children: false
---

## THUNDERMILL01 - Electric Field Sensor for Unmanned Aerial Systems (UAS)

The THUNDERMILL01 is an [electric field mill](https://en.wikipedia.org/wiki/Field_mill) sensor developed for scientific measurements of atmospheric electric fields. It is specifically designed for airborne deployment on UAV platforms, with a focus on real-time monitoring in thunderstorm and atmospheric electricity research.

### Key Features of THUNDERMILL01

* Open-source hardware and software
* Optimized for UAV-borne operations
* Lightweight and mechanically robust
* Real-time data visualization via [TF-ATMON](/instruments/TF-ATMON)
* Proven use on [TF-G2 autogyro](/instruments/TF-G2) during operational scientific missions ([CRREAT project - lightning research](https://crreat.eu/))

## Applications

* **Meteorology:** Local cloud monitoring and atmospheric analysis.
* **Thunderstorm and Weather Research:** Observation of storm-induced electric field variations.
* **Industrial Safety:** Protecting high-value equipment and personnel from electrical discharges.
* **Lightning Warning Systems:** Real-time monitoring for storm-related safety measures.
* **Emergency Management:** Decision support data during severe weather events.
* **HVDC Line Monitoring:** Monitoring of the anomalous electric field for high-voltage DC transmission lines.

### Where to get it?

THUNDERMILL01 can be bought directly from ThunderFly via our [contact email](https://www.thunderfly.cz/contact-us.html). The same email can be used if you have specific requirements for custom modifications or if the product is to be purchased in large quantities.

THUNDERMILL01 was developed in collaboration with [Universal Scientific Technologies s.r.o.](https://www.ust.cz), who contributed to the initial design and continue to support the open-source hardware ecosystem.


## Technical Specifications

Main technical parameters, like resolution and measurement range, could be customized for the specific application required by the customer. 

| Parameter             |Specification        |
| ------------------------------ | --------------------------------------------------- |
| **Measurement Range**          | ±100 kV/m                         |
| **Resolution**                 | 10 V/m                                               |
| **Accuracy**                   | ±5%                                               |
| **Raw Data**                   | Complete waveform capture                                  |
| **Processed Output**           | Electric field intensity                                          
| **E-Field intensity sampling Rate**     | 25 Hz Typical (Depends on RPM)     |
| **Time resolution**            | 521 us (Corresponds to ADC sample rate)|
| **AC Field Immunity**          | Up to 40 dB                                   |
| **Time Tagging**               | Optional integration with [TFGPS01](/avionics/TFGPS01/)  |
| **Motor Type**                 | Ram-powered turbine (e.g., autogyro rotor)   |
| **Dimensions**                 | Cylindrical 80x20mm  |
| **Mass**                       | 34 grams (without cabling) |
| **Mounting Options**           | Autogyro rotor, wing, nose      |
| **Orientation**                | Up-looking (standard) or Side-looking (optional) |
| **EFM Power Input**            | 5V DC @ 100mA   |
| **Power Consumption**          | 0.5 Watt      |
| **Data Interface**             | (Pixhawk 6 pin JST-GH UART Telemetry)[/avionics/TFCAB01/#uarttelemserial-cables]    |
| **Data Visualization**         | [TF-ATMON](/instruments/TF-ATMON) sensor views  |
| **EFM Temperature Range**      | -40°C to 40°C                         |
| **EFM Humidity Range**         | 0–90% RH                                                 |
| **Weatherproof Rating**        | IP44                                              |

### System Diagram

The THUNDERMILL01 sensor is integrated into the TF-ATMON avionics system in the following way:

![THUNDERMILL01 system diagram](TF-ATMON-THUNDERMILL.svg)

### Connector pinouts

![THUNDERMILL01 stator connectors](https://raw.githubusercontent.com/ust-modules/USTTHUNDERMILLPCB01/refs/heads/USTTHUNDERMILLPCB01B/doc/img/USTTHUNDERMILLPCB01A_top.png)

#### TF Payload port

This connector is primarily intended for time synchronization with the [TFGPS01 GNSS receiver](/avionics/TFGPS01), which provides location and time pulse signals (PPS) on its "Payload Connector".


| Signal    | Pixhawk Color                | ThunderFly Color                                  |
| --------- | ------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| TIMEPULSE | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Blue](https://user-images.githubusercontent.com/5196729/102205102-ffbfae00-3eca-11eb-9372-8406f7a4aa9d.png) Blue     |
| EXTINT    | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Yellow](https://user-images.githubusercontent.com/5196729/102204908-bc653f80-3eca-11eb-9a1d-a02ea5481c03.png) Yellow |
| GPIO | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![White](https://user-images.githubusercontent.com/5196729/102204632-5e385c80-3eca-11eb-985d-a881acfae26a.png) White   |
| SDA       | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Green](https://user-images.githubusercontent.com/5196729/102205114-04846200-3ecb-11eb-8eb8-251c7e564707.png) Green   |
| SCL       | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Yellow](https://user-images.githubusercontent.com/5196729/102204908-bc653f80-3eca-11eb-9a1d-a02ea5481c03.png) Yellow |
| TX        | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![White](https://user-images.githubusercontent.com/5196729/102204632-5e385c80-3eca-11eb-985d-a881acfae26a.png) White   |
| RX        | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Green](https://user-images.githubusercontent.com/5196729/102205114-04846200-3ecb-11eb-8eb8-251c7e564707.png) Green   |
| GND       | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black   |

#### J6 - Debug & programming UART Port

The UART interface is compatible with the [Pixhawk connector standard](https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf) as a peripheral device and enables integration with onboard flight controllers. CTS is disconnected, and the RTS signal is used for the MCU reset for bootloader activation. 

| Signal | Pixhawk Color              | ThunderFly Color          |
| ------ | -------------------------- | ---------------------- |
| +5V    | ![Red](https://user-images.githubusercontent.com/5196729/102204855-ab1c3300-3eca-11eb-8083-646d633e3aef.png) Red     | ![Red](https://user-images.githubusercontent.com/5196729/102204855-ab1c3300-3eca-11eb-8083-646d633e3aef.png) Red       |
| RX     | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![White](https://user-images.githubusercontent.com/5196729/102204632-5e385c80-3eca-11eb-985d-a881acfae26a.png) White   |
| TX     | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Green](https://user-images.githubusercontent.com/5196729/102205114-04846200-3ecb-11eb-8eb8-251c7e564707.png) Green   |
| Not connected (CTS)  | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Blue](https://user-images.githubusercontent.com/5196729/102205102-ffbfae00-3eca-11eb-9372-8406f7a4aa9d.png) Blue     |
| RTS    | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Yellow](https://user-images.githubusercontent.com/5196729/102204908-bc653f80-3eca-11eb-9a1d-a02ea5481c03.png) Yellow |
| GND    | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black   |

#### J1 - Pixhawk UART & I2C


| Pin | Signal    | Voltage level | Pixhawk Color    | ThunderFly Color  |
|-----|-----------|---------| -------|---------|
| 1   | VCC       | +5V     | ![Red](https://user-images.githubusercontent.com/5196729/102204855-ab1c3300-3eca-11eb-8083-646d633e3aef.png) Red     | ![Red](https://user-images.githubusercontent.com/5196729/102204855-ab1c3300-3eca-11eb-8083-646d633e3aef.png) Red       |
| 2   | RX (IN)  | +3.3V   | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![White](https://user-images.githubusercontent.com/5196729/102204632-5e385c80-3eca-11eb-985d-a881acfae26a.png) White   |
| 3   | TX (OUT)  | +3.3V   | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Green](https://user-images.githubusercontent.com/5196729/102205114-04846200-3ecb-11eb-8eb8-251c7e564707.png) Green   |
| 4   | I2C SCL   | +3.3V   | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Yellow](https://user-images.githubusercontent.com/5196729/102204908-bc653f80-3eca-11eb-9a1d-a02ea5481c03.png) Yellow |
| 5   | I2C SDA   | +3.3V   | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Green](https://user-images.githubusercontent.com/5196729/102205114-04846200-3ecb-11eb-8eb8-251c7e564707.png) Green   |
| 6   | GND       | GND     | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | ![Black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black   |


### Example of UAV Integration

![THUNDERMILL01 mouted on TF-G2](THUNDERMILL01_UAV_TF-G2_rotor.jpg)

The airborne version of THUNDERMILL01, has been specifically designed for use on unmanned aerial vehicles (UAVs) and is optimized for integration with avionics systems. The design has undergone extensive testing on the [ThunderFly TF-G2 autogyro](/instruments/TF-G2).

* **Mounting**: The sensor is normally mounted close to the autogyro rotor hub, taking advantage of the autogyro's principle to reduce electromagnetic interference and maximize measurement reliability.

* **Data Interface**: The THUNDERMILL01 sensor is typically connected to the [TF-ATMON atmospheric monitoring system](/instruments/TF-ATMON), which handles real-time data acquisition, transmission, and visualization.

* **Telemetry Support**: Using TF-ATMON, data from the sensor is streamed in real-time to a ground station. There, it is displayed in a 3D visualization environment to assist drone operators in decision-making during measurement flights.

* **Use Case**: It is especially suited for operations near thunderclouds, during convective events, or in campaigns investigating the electric field structure of the atmosphere.


### Electromagnetic Considerations for UAV Mounting

Mounting the THUNDERMILL01 on the TF-G2 autogyro has the unique property of an unpowered rotor, which has a very low electromagnetic signature. This allows for cleaner readings of the ambient electric field.

Although the sensor can also be installed on electrically powered multirotor UAVs, such configurations tend to introduce higher levels of electromagnetic noise. In such cases, appropriate shielding and post-processing techniques may be necessary to ensure data quality. Therefore, ram-powered rotation should be preferred where possible.





