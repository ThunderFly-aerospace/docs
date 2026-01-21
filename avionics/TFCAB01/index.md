---
layout: page
title: "TFCAB01: ThunderFly Pixhawk Compatible Cabling System"
permalink: /avionics/TFCAB01/
parent: "Communication & Interfaces"
nav_order: "50"
---

# TFCAB - ThunderFly Pixhawk Compatible Cabling System

TFCABxxyy01 cables are high-quality silicone cables designed for avionics applications in Pixhawk-based drone systems. These cables ensure reliable connectivity, enhanced mechanical resistance, and reduced electromagnetic interference (EMI). Each cable type follows a structured color-coding scheme to ensure easy identification and reduce connection errors.

## Available Cable Variants

ThunderFly offers three main cable types:
- **I²C Cables**: Used for I²C bus communication.
- **UAVCAN Cables**: Designed for CAN bus communication.
- **UART/TELEM/SERIAL Cables**: Used for serial data transmission.

Each cable type is available in different lengths (15 cm, 30 cm, and 45 cm). All cables use **JST-GH connectors** for robust and secure connections. All cables could be purchased on correspondin links or via direct email inquiry at sale@thunderfly.cz.

## I²C Cables

The TFCABxxI2C01 series is optimized for **I²C communication**, featuring a twisted design to minimize internal cross-talk and capacitance. This ensures reliable data transmission in avionics environments.

![TFCABxxI2C01](https://user-images.githubusercontent.com/5196729/234793444-a4d4c73b-5eb9-4614-a92b-722d95fa6c30.jpg)

## Where to Buy

TFCAB I2C cables can be purchased from:

  * [Lectronz](https://lectronz.com/products/1060)
  * [Tindie](https://www.tindie.com/products/30113/)

### Specifications

- **Lengths**: 15 cm, 30 cm, 45 cm
- **Connector Type**: JST-GH
- **Number of Pins**: 4
- **Designed for**: I²C bus

### Pinout and Color Coding

| Pin Number | ThunderFly Color | Signal |
|------------|-----------------|--------|
| 1          | ![red](https://user-images.githubusercontent.com/5196729/102204855-ab1c3300-3eca-11eb-8083-646d633e3aef.png) Red | VCC (5.4V) |
| 2          | ![yellow](https://user-images.githubusercontent.com/5196729/102204908-bc653f80-3eca-11eb-9a1d-a02ea5481c03.png) Yellow | SCL |
| 3          | ![green](https://user-images.githubusercontent.com/5196729/102205114-04846200-3ecb-11eb-8eb8-251c7e564707.png) Green | SDA |
| 4          | ![black](https://user-images.githubusercontent.com/5196729/102204896-b8d1b880-3eca-11eb-8b73-656cac9104e4.png) Black | GND |

### Cable Twisting
- **10 turns per 30 cm** for SCL/VCC and SDA/GND pairs.
- **4 turns per 30 cm** for the combined cable.

## UAVCAN Cables

The TFCABxxCAN01 series is designed for **UAVCAN communication**, optimized for EMI resistance through specific cable twisting.

## Where to Buy

TFCAB CAN cables can be purchased from:

  * [Lectronz](https://lectronz.com/products/1195)
  * [Tindie](https://www.tindie.com/products/30124/)


### Specifications

- **Lengths**: 15 cm, 30 cm, 45 cm
- **Connector Type**: JST-GH
- **Number of Pins**: 4
- **Designed for**: CAN bus

### Pinout and Color Coding

| Pin Number | ThunderFly Color | Signal |
|------------|-----------------|--------|
| 1          | ![red](https://user-images.githubusercontent.com/5196729/102204855-ab1c3300-3eca-11eb-8083-646d633e3aef.png) Red | VCC (5.4V) |
| 2          | ![white](https://user-images.githubusercontent.com/5196729/102204632-5e385c80-3eca-11eb-985d-a881acfae26a.png) White | CAN_H |
| 3          | ![yellow](https://user-images.githubusercontent.com/5196729/102204908-bc653f80-3eca-11eb-9a1d-a02ea5481c03.png) Yellow | CAN_L |
| 4          | ![black](https://user-images.githubusercontent.com/5196729/102204896-b8d1b880-3eca-11eb-8b73-656cac9104e4.png) Black | GND |

### Cable Twisting

- **10 turns per 30 cm** for GND/VCC and CAN_L/CAN_H pairs.
- **4 turns per 30 cm** for the combined cable.

## UART/TELEM/SERIAL Cables

The TFCABxxUART01 series is used for **serial communication**, connecting autopilots and peripherals. UART cables do not support networking and must be connected directly.

### Specifications
- **Lengths**: 15 cm, 30 cm, 45 cm
- **Connector Type**: JST-GH
- **Number of Pins**: 6
- **Designed for**: Serial (UART, TELEM, etc.)

### Pinout and Color Coding

| Pin Number | ThunderFly Color | Signal |
|------------|-----------------|--------|
| 1          | ![red](https://user-images.githubusercontent.com/5196729/102204855-ab1c3300-3eca-11eb-8083-646d633e3aef.png) Red | VCC (5.4V) |
| 2          | ![white](https://user-images.githubusercontent.com/5196729/102204632-5e385c80-3eca-11eb-985d-a881acfae26a.png) White | TX |
| 3          | ![green](https://user-images.githubusercontent.com/5196729/102205114-04846200-3ecb-11eb-8eb8-251c7e564707.png) Green | RX |
| 4          | ![blue](https://user-images.githubusercontent.com/5196729/102205102-ffbfae00-3eca-11eb-9372-8406f7a4aa9d.png) Blue | CTS |
| 5          | ![yellow](https://user-images.githubusercontent.com/5196729/102204908-bc653f80-3eca-11eb-9a1d-a02ea5481c03.png) Yellow | RTS |
| 6          | ![black](https://user-images.githubusercontent.com/5196729/102205213-28e03e80-3ecb-11eb-95bb-7ba207360541.png) Black | GND |

### Important Notes
- **UART cables should be kept as short as possible** to minimize EMI interference.
- **Twisting is not recommended** for UART cables to prevent increased cross-talk.
- **Straight-through wiring**: Ensure that RX/TX and RTS/CTS are properly swapped in devices.


### SPI

|Signal| Pixhawk Color | ThunderFly color |
|--------|------------------|---------------------|
| +5V  |     Red    |   ![red](https://user-images.githubusercontent.com/5196729/102204855-ab1c3300-3eca-11eb-8083-646d633e3aef.png)  Red   |
| SCK  |    Black  |    ![yellow](https://user-images.githubusercontent.com/5196729/102204908-bc653f80-3eca-11eb-9a1d-a02ea5481c03.png)  Yellow | 
| MISO |   Black  |   ![blue](https://user-images.githubusercontent.com/5196729/102205102-ffbfae00-3eca-11eb-9372-8406f7a4aa9d.png) Blue  | 
| MOSI |   Black  |   ![green](https://user-images.githubusercontent.com/5196729/102205114-04846200-3ecb-11eb-8eb8-251c7e564707.png) Green | 
| CS!  |     Black  |  ![white](https://user-images.githubusercontent.com/5196729/102204632-5e385c80-3eca-11eb-985d-a881acfae26a.png) White | 
| CS2 |    Black   | ![blue](https://user-images.githubusercontent.com/5196729/102205102-ffbfae00-3eca-11eb-9372-8406f7a4aa9d.png)  Blue | 
| GND |   Black   |   ![black](https://user-images.githubusercontent.com/5196729/102204896-b8d1b880-3eca-11eb-8b73-656cac9104e4.png) Black  |

