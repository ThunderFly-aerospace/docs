---
layout: page
title: "TFSIK02: Secure High‑Power Telemetry Modem"
permalink: /avionics/TFSIK02/
parent: "Communication & Interfaces"
nav_order: "11"
---

# TFSIK02 – Secure High‑Power Telemetry Modem

### Purchasing Information

The device can be purchased from ThunderFly s.r.o. For commercial quotations or special configurations (frequency bands, output power, cryptographic handling), contact us at [sale@thunderfly.cz](mailto:sale@thunderfly.cz).
TFSIK02 is developed and manufactured in‑house and localised in the EU, which allows  hardware configuration and traceable customization required by defense and security‑sensitive users.

## Overview

TFSIK02 is a European-made defense‑oriented variant of the TFSIK telemetry modem, designed for secure and long-range command, control, and telemetry links (UAV C2 link) in environments where interference resistance, controlled frequency allocation, and link confidentiality are primary requirements.

While TFSIK02 is technically derived from the [TFSIK01](/avionics/TFSIK01) design, it is not intended  for hobby or civil UAV telemetry. Instead, it targets:

* Defense and security UAVs
* Government and institutional unmanned systems
* Applications where key management and link isolation are required

For general SiK firmware operation, radio principles (FHSS, TDM, LBT), and AT‑command configuration, refer to the corresponding sections in the [TFSIK01 documentation](/avionics/TFSIK01).

## Designed for Defense Use

Compared to [TFSIK01](/avionics/TFSIK01), TFSIK02 emphasizes:

* **High RF output power**  - up to 35 dBm, using robust hardware Power Amplifier
* **Controlled frequency planning** - outside standard hobby ISM usage
* **Dual‑antenna diversity** - for spatial robustness
* **FHSS + TDM architecture** - resilient against narrowband jamming
* **Multiple AEAD encryption and key‑handling concepts** - Explicit cryptographic workflows detailed in description below
* **Point‑to‑point operational model** - solves encrypted transmission between the two UART Telemetry ports (UAV <-> GCS)
* **Deterministic link pairing** - removes accidental association with third‑party radios

Generic SiK firmware features are described in the [TFSIK01 documentation](/avionics/TFSIK01) and are not repeated here. The modem remains based on open and inspectable hardware and firmware principles, which allows security audits and controlled deployment, while avoiding black‑box radio behavior.


## Hardware Parameters

| Parameter             | Value                      | Notes                                            |
| --------------------- | -------------------------- | ------------------------------------------------ |
| Frequency range       | 142 MHz – 1050 MHz         | Factory configured, band‑specific RF front‑end   |
| RF output power       | 20 dBm – 35 dBm            | Fixed per configuration, regulatory dependent    |
| Receiver sensitivity  | ≤ −117 dBm                 | 64 kbps air data rate                         |
| RF bandwidth          | < 4 MHz                    | Hardware‑filtered                                     |
| Antenna connectors    | MCX (dual)                 | Supports diversity                               |
| Interface             | 3.3 V UART (JST‑GH)        | Pixhawk‑compatible                               |
| Supply voltage        | 5 V                        | Power consumption depends on RF power (Up to 2A) |
| Operating temperature | −20 °C to +40 °C           | Cooling‑limited                                  |

## Frequency Bands of Interest for Defense Users

| Nominal Band    | Typical Use Case                   |
| --------------- | ---------------------------------- |
| **225–400 MHz** | Military UHF / long‑range LOS      |
| **400–450 MHz** | Tactical UAV telemetry             |
| **433 MHz**     | Shared / experimental environments |
| **460–500 MHz** | Government‑allocated channels      |
| **800–900 MHz** | High‑throughput short‑range links  |
| **915 MHz**     | Export‑friendly configurations     |

⚠️ Regulatory compliance is entirely deployment‑dependent. TFSIK02 hardware is configured per project and not user‑retunable across bands.


#### Example of software parameters 

The TFSIK02 parameters could be read exactly the same as in [TFSIK01 documentation](/avionics/TFSIK01).

    picocom /dev/ttyUSB0 -b 57600
    +++
    OK
    ATI5
    S0:FORMAT=26
    S1:SERIAL_SPEED=57
    S2:AIR_SPEED=64
    S3:NETID=25
    S4:TXPOWER=35
    S6:MAVLINK=1
    S7:OPPRESEND=0
    S8:MIN_FREQ=433050
    S9:MAX_FREQ=434790
    S10:NUM_CHANNELS=10
    S11:DUTY_CYCLE=100
    S12:LBT_RSSI=0
    S13:MANCHESTER=0
    S14:RTSCTS=0
    S15:MAX_WINDOW=131
    S16:ENCRYPTION_LEVEL=1

In addition to these standard parameters. The TFSIK02 has the following encryption features: 

#### Encryption key setup

The encryption level stored in `S16` picks the key length, so set it before writing the key (1 → 128 bit/32 hex chars, 2 → 192 bit/48 hex chars, 3 → 256 bit/64 hex chars). Example for a 128‑bit key:

```
+++
OK
ATS16=1          # select 128-bit key
AT&E=00112233445566778899AABBCCDDEEFF   # set key (32 hex chars)
AT&E?            # read back the key
AT&W             # save to flash
ATZ              # reboot to apply
```

##### One-Time-Pad (Vernam) Encryption Mode

For special defense deployments, TFSIK02 can operate in an optional [Vernam (One-Time-Pad) encryption mode](https://en.wikipedia.org/wiki/One-time_pad) using a pre-generated random key stream stored on external memory. The key material is prepared before deployment for the full mission duration and loaded into both the UAV and ground modem under controlled conditions.

During operation, telemetry data on the UART interface is encrypted by a direct XOR operation with the continuously read key stream. Both endpoints consume keys sequentially from a prepared external memory. No over-the-air key exchange or algorithm negotiation takes place.

```
+++
OK
ATS16=200        # select Vernam OTP mode
AT&W             # save to flash
ATZ              # reboot to apply
```
The key sequence is then read after powering up from external media. 

This mode provides the highest possible information confidentiality independent of computational attack capability (including quantum computing). It is therefore suitable for environments where a minimal algorithmic attack surface is required. But operational discipline is essential. Key material must be securely generated, distributed, protected, and permanently destroyed after use. Reuse of key segments invalidates security.

## Secure Communication and Encryption Concepts

TFSIK02 supports multiple encryption and key‑management models, depending on how the modem pair is deployed and integrated. Its general principle is drop-in replacement of an unencrypted Mavlink modem connected on UART, by an encrypted wireless datalink between two UART ports. 

### Fixed Paired Modems (Pre‑Shared Key)

In the simplest and most robust model, TFSIK02 is delivered as a fixed modem pair:

* One modem for the UAV (UAS)
* One modem for the Control / Ground Station (CGS)

Both modems share a pre‑programmed cryptographic key set during manufacturing. The pair is intended to operate exclusively with each other.

**Advantages:** Maximum simplicity, no field configuration required, Minimal attack surface.
**Typical use:** single‑mission platforms, expendable UAVs, classified environments.

### QR‑Code / Label‑Based Key Provisioning

In this model, each UAV modem carries a unique cryptographic key, represented as a machine‑readable code (QR / DataMatrix) on a physical label attached to the device.

  * The UAV modem is installed on the airframe
  * The operator reads the code from the label
  * The CGS modem is configured with the corresponding key before the mission

**Advantages:** Field pairing without digital interfaces. No wireless key exchange. Suitable for logistics‑heavy operations.
**Typical use:** small series UAVs, mixed fleets, forward deployment.

### Dynamic Key Management (Per‑Flight Keys)

For reusable UAV platforms, TFSIK02 can be integrated into a higher‑level key‑management system, where:

* A new cryptographic key is generated for each mission
* Keys are injected via secure ground infrastructure
* Lost or captured UAVs do not compromise future links

This model assumes the existence of a trusted pre‑deployment infrastructure, procedural control over the entire cryptographic key lifecycle, and integration at the system level rather than relying on modem‑only configuration.

**Advantages:** Highest security level, Compartmentalization of missions
**Typical use:** reusable defense UAVs, long‑term platforms.

## Threat Model

### Unauthorized Pairing and Link Takeover

Unauthorized pairing of third‑party radios is prevented at the cryptographic level. A TFSIK02 modem will only establish a functional link if the peer modem possesses the correct cryptographic key. Without the valid key, received frames are discarded, and no valid telemetry or command stream is produced.

As a consequence, passive eavesdropping using SDR receivers yields encrypted data only, while active attempts to inject or replay packets fail without knowledge of the cryptographic key. Accidental pairing with foreign or third‑party SiK‑based radios is, therefore, effectively impossible. This makes common SDR‑based penetration techniques (traffic replay, packet injection, blind fuzzing) ineffective unless the cryptographic configuration is compromised.

### Loss or Capture of UAV

Loss of the UAV platform does not automatically compromise the communication system. When using per‑flight or short‑lived keys:

* Keys used during a mission are not reused
* Compromise of one UAV does not affect other vehicles
* Future missions remain secure

For higher security requirements, TFSIK02 can be configured such that cryptographic keys are stored only in volatile memory. In this mode, keys are erased immediately upon power loss, and physical capture of an unpowered UAV does not reveal past or future keys.

### Key Lifecycle Assumptions

The overall security of the system depends on correct operational key handling, including:

* Secure generation of keys
* Controlled key injection into UAV and CGS
* Proper destruction of expired keys

TFSIK02 provides the technical mechanisms to support these workflows, while procedural enforcement remains the responsibility of the operator.

## Installation and Integration Notes

Mechanical installation, antenna placement, and UART wiring follow the same principles as described in the [TFSIK01](/avionics/TFSIK01) Hardware Setup and Installation sections. Only band‑specific antenna systems and RF power considerations differ.

## Export and Use Disclaimer

TFSIK02 is not a consumer or hobby telemetry device. It is supplied exclusively for professional, institutional, or governmental users who are responsible for frequency allocation, regulatory compliance, and cryptographic policy. Because it is designed for professional, governmental, and defense‑related applications. For civil and research UAV applications, refer to [TFSIK01](/avionics/TFSIK01). Depending on the selected frequency band, output power, and cryptographic configuration, the device may be subject to export control.

The responsibility for the following activities rests solely with the user or purchasing organization.

* Compliance with national and international regulations
* Frequency allocation and licensing
* Cryptographic policy and approval

ThunderFly s.r.o. supplies TFSIK02 as a configurable hardware platform. Final system classification, certification, and lawful use depend on how the device is integrated and deployed.




