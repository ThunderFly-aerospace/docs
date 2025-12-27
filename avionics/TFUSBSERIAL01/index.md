---
layout: page
title: "TFUSBSERIAL01 - USB Serial Telemetry Interface"
permalink: /avionics/TFUSBSERIAL01/
parent: "Communication & Interfaces"
nav_order: "4"
---

# TFUSBSERIAL01 - USB-C to serial converter with Pixhawk telemetry connectors

The converter is designed to service and debug operations on UAVs. It respects the [Pixhawk DS-009](https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf) connector standard.

![TFUSBSERIAL01 Enclosure](TFUSBSERIAL01.JPG)

## Key features

  * Could be connected to both the peripheral and FMUs
  * The FMU and peripheral connectors are separated; therefore, there is no need for a special RX/TX cross-cable
  * Could be used for sniffing serial communication on telemetry links between autopilot and its peripheral (Both connectors could be used at once)
  * Supports hardware flow control
  * The power delivered from USB is protected from excess current, possibly drawn by the peripheral or FMU
  * The accidental power from the FMU to the USB is protected by a reverse diode

## How to Buy

- Direct order — Email [sale@thunderfly.cz](mailto:sale@thunderfly.cz) to request quotations, customization details, or volume pricing provided by ThunderFly s.r.o.
- [Purchase TFUSBSERIAL01 on Lectronz](https://lectronz.com/products/1066) for streamlined EU fulfillment.
- [Purchase TFUSBSERIAL01 on Tindie](https://www.tindie.com/products/34364/) for worldwide availability.


### Usage

Connect the FMU or peripheral device to the corresponding PixHawk connector.  The standard serial terminal tools could be used for communication with the devices. 

### Self-test

The proper function and cable could be easily tested by connecting the cable between the "to FMU" and "to Peripheral" connectors.

![TFUSBSERIAL01 self test](https://raw.githubusercontent.com/ThunderFly-aerospace/TFUSBSERIAL01/TFUSBSERIAL01A/doc/img/TFUSBSERIAL01_self-test.jpg)

All communication sent by UART is, in that case, forwarded in the loop. Therefore, the cable behaves the same as "local echo".
