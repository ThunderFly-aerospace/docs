---
layout: page
title: "TFFLIP2PH - Flipper Zero to Pixhawk Peripheral Adapter"
permalink: /tools/TFFLIP2PH/
parent: "Development Tools"
nav_order: 10
---

# TFFLIP2PH - Flipper Zero to Pixhawk (Dronecode standard) peripheral adapter 

TFFLIP2PH is a compact hardware adapter designed to connect [Flipper Zero](https://en.wikipedia.org/wiki/Flipper_Zero) with Pixhawk-compatible peripherals. The board allows rapid sensor prototyping, testing, and demonstration using Flipper Zero as an interface device.

## Features

- **Flipper Zero GPIO** to **Pixhawk-compatible JST-GH connectors**
- **Supported Interfaces**:
  - **UART** (for peripheral devices, telemetry, and modems)
  - **I2C** (for sensors)
  - **SPI** (for high-speed sensors)
  - **PWM** (for RC servos and basic actuator testing)
- **5V Peripheral Power Supply** (sourced from Flipper Zero)
- Compact design suitable for flat sensor mounting on the back of Flipper Zero
- Designed as a [Small External Module](https://docs.flipper.net/zero/development/hardware/modules-blueprints#NIlXe)

## Typical Use Cases

- Rapid prototyping of sensor drivers with Flipper Zero
- Bringing up new hardware using UART, I2C, or SPI
- Laboratory testing and control
- Educational and demonstration purposes
- Basic servo testing via PWM ([Example: flipper-servotester](https://github.com/ThunderFly-aerospace/flipper-servotester))
- Internal testing and QA tooling

## Construction Notes

- Peripheral connectors follow Pixhawk (Dronecode) standard pinouts
- Peripheral power output: 5V @ 1A (max)
- Power is sourced from the Flipper Zero switching power supply
- User responsibility:
  - Verify max current consumption
  - Ensure voltage compatibility
  - Check signal level requirements of connected devices

## Mechanical Concept

The TFFLIP2PH board is designed to be mounted flat on top of Flipper Zero, with connectors oriented parallel to the PCB surface. This allows attached peripherals to be securely fixed using  adhesive tape or hook-and-loop fasteners on the back of Flipper Zero, making it suitable for portable experimentation.

### "Flight Controller" Mode

In this configuration, Flipper Zero acts as the flight controller emulator, and the connected devices are peripherals.

![TFFLIP2PH top view](https://raw.githubusercontent.com/ThunderFly-aerospace/TFFLIP2PH/refs/heads/TFFLIP2PH-A/doc/gen/img/TFFLIP2PH-top.png)

### TF Payload Mode

In this mode, Flipper Zero is used as a payload device, connected between a TF Payload connector (available on [TFGPS](/avionics/TFGPS01/)) and a flight controller.

![TFFLIP2PH bottom view](https://raw.githubusercontent.com/ThunderFly-aerospace/TFFLIP2PH/refs/heads/TFFLIP2PH-A/doc/gen/img/TFFLIP2PH-bottom.png)

## How to Order

You can order TFFLIP2PH and other ThunderFly tools in the following ways:

- Directly from ThunderFly — use our [Contact Us](https://www.thunderfly.cz/contact-us.html) page to request a quotation, check lead times, or discuss bulk pricing.
- Online marketplaces:
  - [Tindie](https://www.tindie.com/stores/thunderfly/) — suitable for worldwide orders
  - [Lectronz](https://lectronz.com/stores/thunderfly) — recommended for customers in Europe.
