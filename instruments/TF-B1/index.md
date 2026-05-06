---
title: "TF-B1 - Stratospheric Balloon Experimental Platform"
layout: page
permalink: /instruments/TF-B1
parent: Instrument Platforms
nav_order: "2"
---

# TF-B1 - Stratospheric Balloon Experimental Platform

The [TF-B1](https://github.com/ThunderFly-aerospace/TF-B1) stratospheric balloon is a versatile high-altitude experimental platform designed for several-hour flights to altitudes around 30 km. It serves as a universal carrier for atmospheric research, technology validation, and educational projects. Built on proven ThunderFly avionics modules, TF-B1 provides reliable performance in near-space conditions, offering a cost-effective alternative to satellite testbeds.

![Example of experimental gondola](https://raw.githubusercontent.com/ODZ-UJF-AV-CR/FIK-6/refs/heads/FIK-6/doc/img/FIK-6_gondola_weight.jpg)


## Main design highlights

* Ready-to-use integration with [TF-ATMON atmospheric monitoring system](/instruments/TF-ATMON)
* Redundant telemetry link via [TFSIK01 communication system](/avionics/TFSIK01)
  * Backup by LoRa, using [TFLORA01 modem](/avionics/TFLORA01)
* Onboard positioning and timing with [TFGPS01](/avionics/TFGPS01)
* Gondola orientation tracking
* Atmospheric sensing with [TFHT01](/avionics/TFHT01) or [TFHT02](/avionics/TFHT02)
  * Number of sensors is highly expandable by use of [TFI2CADT01](/avionics/TFI2CADT01)
* Reliable power distribution using [TFSBEC01 power module](/avionics/TFSBEC01)
  * Designed for relatively high-power payloads up to tens of Watts
* Support for scientific instruments with [TFUNIPAYLOAD01 payload interface](/avionics/TFUNIPAYLOAD01)
* Continuous pre-flight charging and power monitoring for maximal uptime
  * Ground monitoring direcly by [TFUSBSERIAL01](/avionics/TFUSBSERIAL01)

## Reference flights

TF-B1 has been successfully deployed in multiple missions:

* [FIK-10 flight](https://github.com/ODZ-UJF-AV-CR/FIK-10)
* [FIK-9 experiment](https://github.com/ODZ-UJF-AV-CR/FIK-9)
* [FIK-6 high-altitude balloon flight](https://github.com/ODZ-UJF-AV-CR/FIK-6)
* [FIK-5 experiment](https://github.com/ODZ-UJF-AV-CR/FIK-5)


The result from these missions is the following scientific paper [MEASUREMENT OF THE REGENER-PFOTZER MAXIMUM USING DIFFERENT TYPES OF IONISING RADIATION DETECTORS AND A NEW TELEMETRY SYSTEM TF-ATMON](https://pubmed.ncbi.nlm.nih.gov/36005953/)


## Applications

### Atmospheric research

TF-B1 enables high-resolution measurements of temperature, humidity, and gas composition in the stratosphere. Using ThunderFly’s [TFHT01](/avionics/TFHT01) and [TFHT02](/avionics/TFHT02) sensors, vertical atmospheric profiles can be collected for improved weather prediction models and climate studies.

### Aerospace and materials testing

The balloon gondola provides near-space conditions such as an isolated environment, extreme temperatures, and increased radiation. This environment is ideal for testing spacecraft components, electronics, and materials before deployment in orbit.

### Educational and outreach missions

TF-B1 offers an accessible way for students and researchers to conduct real high-altitude experiments. Short-duration flights allow hands-on experience in instrumentation, avionics, and atmospheric sciences.


## Professional support

Professional support for the ThunderFly TF-B1 stratospheric balloon platform is commercially available from [ThunderFly s.r.o.](https://www.thunderfly.cz/). For inquiries, contact us at **[info@thunderfly.cz](mailto:info@thunderfly.cz)**.



## Technical specifications

| Parameter | Typical value | Notes |
|------------|----------------|-------|
| **Maximum altitude** | 30 km | Verified in test flights |
| **Payload capacity** | up to 2 kg | Depends on balloon size and helium fill |
| **Flight duration** | 2–4 hours | Depending on ascent rate and burst altitude |
| **Ascent rate** | 5–6 m/s | Typical for 2 kg payload with 1200–1600 g latex balloon |
| **Descent system** | Parachute recovery | Automatically deployed after burst |
| **Operating temperature range** | –60 °C to +40 °C | Electronics rated for stratospheric conditions |
| **Power supply** | Li-ion battery pack, 7.2 V nominal | Managed by [TFSBEC01](/avionics/TFSBEC01) |
| **Telemetry** | TFSIK01 (primary), TFLORA01 (backup) | Redundant communication systems |
| **Positioning** | TFGPS01 GNSS receiver | Continuous location and altitude tracking |
| **Sensor integration** | TFHT01 / TFHT02 / TF-ATMON | Atmospheric and environmental sensors |
| **Data logging** | Onboard SD storage + real-time telemetry | Supports full mission replay |
| **Structure** | EPP/foam gondola with modular avionics bay | Shock-resistant and lightweight |
| **Launch method** | Free balloon launch with tether release | Compliant with national aviation regulations |
| **Recovery** | GNSS-based tracking beacon | Enables field retrieval |

![Block diagram](https://raw.githubusercontent.com/ThunderFly-aerospace/TF-B1/refs/heads/main/doc/img/block_schematics.png)


## LoRa Beacon Configuration

TF-B1 includes a long-range recovery beacon implemented using the [TFLORA01 LoRa modem](/avionics/TFLORA01/). The beacon periodically transmits a compact GPS telemetry packet that allows recovery of the payload even when the primary telemetry link is unavailable.

The LoRa subsystem is implemented using two software modules. Only the application layer is platform-specific:

**`tflora`**
Low-level LoRa PX4 driver based on the LMIC stack. Responsible for radio configuration, packet transmission, spreading factor control, and scheduling of radio activity. This module is a generic TFLORA01 driver and is intended to remain unchanged across different platforms. For the configuration of this software module looks in [TFLORA01 documentation](/avionics/TFLORA01/).

**`lora_gps_vcmd`**
Application layer used in TF-B1. This module generates the beacon message, encodes GPS telemetry into a compact binary format, and schedules periodic transmissions. It also implements a dual spreading-factor operation used to balance transmission range and airtime.

#### PX4 Parameters

The `lora_gps_vcmd` module uses PX4 parameters to control the LoRa GPS beacon transmission interval. Parameter updates are monitored during runtime and applied without restarting the module.

| Parameter      | Group | Default | Range    | Description                                                |
| -------------- | ----- | ------- | -------- | ---------------------------------------------------------- |
| `LORA_GPS_INT` | LoRA  | 120     | 20–86400 | Interval between LoRatransmissions in seconds. |

The module checks the elapsed time since the last transmission once the configured interval has passed.

### Beacon Transmission

The beacon periodically transmits a compact navigation packet containing the latest navigation data. The firmware may alternate between two spreading factors to increase the probability of reception at long distances while maintaining acceptable airtime.

### Beacon Payload Format

The used LoRa frame contains a fixed-size binary structure optimized for minimal payload length. Total payload size is 17 bytes.

```
Byte offset
0   1       5       9     11    13    15    17
+---+-------+-------+-----+-----+-----+-----+
|Flg|  Lat  |  Lon  | Age | Alt | Crs | Spd |
+---+-------+-------+-----+-----+-----+-----+
```

| Offset | Size | Field             |
| ------ | ---- | ----------------- |
| 0      | 1    | Flags             |
| 1–4    | 4    | Latitude (int32)  |
| 5–8    | 4    | Longitude (int32) |
| 9–10   | 2    | GPS age           |
| 11–12  | 2    | Altitude          |
| 13–14  | 2    | Course            |
| 15–16  | 2    | Speed             |


#### Field Description

| Field     | Type   | Description                |
| --------- | ------ | -------------------------- |
| Type / Flags  | uint8  | Packet type identifier or navigation validity flags |
| Latitude  | int32  | Latitude scaled by 2²²     |
| Longitude | int32  | Longitude scaled by 2²²    |
| GPS age   | uint16 | Age of GPS solution [s]    |
| Altitude  | int16  | Altitude above MSL [m]     |
| Course    | uint16 | Course over ground         |
| Speed     | uint16 | Ground speed               |

Latitude and longitude use a fixed-point representation:

```
encoded = coordinate_deg × 2^22
```

This encoding provides sub-meter resolution while keeping the payload small.

#### Flags byte

```
bit7 bit6 bit5 bit4 bit3 bit2 bit1 bit0
 +----+----+----+----+----+----+----+----+
 | Packet type identifier      | V  |  F |
 +----+----+----+----+----+----+----+----+
```

Where bit meanings are:

| Bit | Meaning               |
| --- | --------------------- |
| 4-7 | Housekeeping telemetry packet (0xF0) or Navigation beacon packet |  
| F   | GPS fix available     |
| V   | Navigation data valid |


### The Things Network Decoder Example

For integration with [The Things Network (TTN)](https://www.thethingsnetwork.org/), the following JavaScript decoder can be used to convert the binary LoRa payload into structured telemetry fields. The decoder runs on the server and interprets the received byte array.

```

function Decoder(b, port) {
  if (b[0] == 0xf0) {
    var temperature;
    var current;
    var battery_voltage = b[1] + 175;
    var current_sign = b[3] & 1;
    var battery_current = b[2];
    if (current_sign) {
      current = 0xFFFFFF00 | battery_current;  // fill in most significant bits with 1's
    }
    else {
      current = battery_current;
    }
      
    var voltage = battery_voltage / 100;
    
    var temp = b[3] >> 1;
    var temp_sign = b[3] >> 7;
    if (temp_sign) {
      temperature = 0xFFFFFF80 | temp;  // fill in most significant bits with 1's
    }
    else {
      temperature = temp;
    }
    
    var hits = b[4] + (b[5] << 8);
    
    return {
      'V' : voltage,
      'mA' : current,
      '°C' : temperature,
      'hits' : hits
    };
  }
  else {
    var lat = (b[1]<<24)|(b[2]<<16)|(b[3]<<8)|b[4];
    var lon = (b[5]<<24)|(b[6]<<16)|(b[7]<<8)|b[8];
    var latlon_age = (b[9]<<8)|b[10];
    var alt = (b[11]<<8)|b[12];
    var course = (b[13]<<8)|b[14];
    var speed = (b[15]<<8)|b[16];
    
    var decoded = {
      "lat": lat/4194304.0,
      "lon": lon/4194304.0,
      "latlon_ok": b[0]&0x01,
      "latlon_age_s": latlon_age,
      "alt_m": alt,
      "alt_okay": (b[0]>>1)&0x01,
      "course": course/64.0,
      "course_ok": (b[0]>>3)&0x01,
      "speed_mps": speed/16.0,
      "speed_ok": (b[0]>>4)&0x01
    };
    return decoded;
  }
}
```

The decoder distinguishes two packet types based on the first byte:

* **`0xF0` telemetry packet** – used for housekeeping data such as battery voltage, current, temperature, and detector hit counters.
* **Navigation beacon packet** – all other values of the first byte are interpreted as the navigation payload described above.

The boolean fields such as `latlon_ok`, `alt_okay`, `course_ok`, and `speed_ok` are derived from the flag bits stored in the first byte of the payload. These flags indicate whether the corresponding measurements were valid at the time of transmission. Even when a measurement is marked invalid, the payload may still contain the last available numeric value; therefore, applications should always check the validity flags before using the decoded data.

The decoder operates purely on the application payload and is independent of the LoRaWAN regional parameters. The same payload structure can therefore be used globally, regardless of the radio-frequency plan or regional network configuration.
