---
title: "TF-simulator - Mission Training Toolchain"
layout: page
permalink: /instruments/TF-simulator
parent: Instruments
nav_order: "5"
---

# TF-simulator - Mission Training and Atmospheric Measurement Simulator

The **TF-simulator** is a solution combining atmospheric measurement and flight mission simulation. It bridges two complementary systems:

* **[TF-ATMON](/instruments/TF-ATMON)**: ThunderFly’s toolchain for in-flight atmospheric measurements using UAVs.
* **[PX4-FlightGear-Bridge](https://github.com/ThunderFly-aerospace/PX4-FlightGear-Bridge)**: A simulation environment based on [FlightGear](https://www.flightgear.org/), enabling advanced training and mission rehearsal.

Together, these tools provide both environmental data collection and realistic UAV mission training, suitable for research, education, and operator preparation.

![TF-simulator screenshot](https://raw.githubusercontent.com/PX4/PX4-FlightGear-Bridge/master/art/screenshot.png)

## How TF-simulator Works

The TF-simulator leverages the **PX4-FlightGear-Bridge** to connect the PX4 autopilot software stack with the FlightGear simulator. FlightGear provides:

* Realistic flight dynamics for multiple UAV models (including [TF-G1](https://github.com/ThunderFly-aerospace/TF-G1) and [TF-G2](/instruments/TF-G2) autogyros).
* Advanced weather and environment simulations.
* Support for training missions in diverse conditions.

Meanwhile, TF-ATMON complements this environment by offering real sensor integration and payload data handling, making the simulator not just a training tool but also a platform for testing measurement workflows.

## Vendor Information

The TF-simulator, including professional support, is provided by [ThunderFly s.r.o.](https://www.thunderfly.cz/).

For inquiries, training, or paid support options, contact: **[sale@thunderfly.cz](mailto:sale@thunderfly.cz)**

## Key Features

* **Mission rehearsal**: Test complex UAV flight plans in a safe environment.
* **Sensor simulation**: Integrate TF-ATMON-compatible payloads for realistic workflows.
* **Environmental modeling**: Use FlightGear’s advanced weather scenarios.
* **Model library**: Support for autogyros, airplanes, and rovers.
* **Open ecosystem**: Based on open-source PX4 and FlightGear projects.

## Supported UAV Models

| Vehicle                                                           | Description                      |
| ----------------------------------------------------------------- | -------------------------------- |
| [TF-G1](https://github.com/ThunderFly-aerospace/FlightGear-TF-G1) | Autogyro UAV simulation          |
| [TF-G2](/instruments/TF-G2)                                       | Advanced autogyro UAV simulation |
| [TF-R1](https://github.com/ThunderFly-aerospace/TF-R1)            | UAV Ground-station rover model               |
| Rascal airplane                                                   | Fixed-wing simulation            |

## Support and Services

ThunderFly provides **paid support** for:

* Simulator setup and customization.
* Integration of new UAV models (defined in [YASim](https://wiki.flightgear.org/YASim)).
* Mission training packages.
* Research collaborations.

Contact ThunderFly for tailored solutions at [info@thunderfly.cz](mailto:info@thunderfly.cz).

