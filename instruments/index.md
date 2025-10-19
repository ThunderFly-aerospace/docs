---
layout: page
title: Instruments
alt_text: ThunderFly Instruments
permalink: /instruments/
has_children: true
nav_order: 10
---

## Design for Interoperability

ThunderFly instruments are designed as a toolset that spans the entire mission lifecycle: airframe preparation, in-flight control, telemetry, data acquisition, and post-flight analysis.  Each platform leverages shared avionics, communication protocols, and payload interfaces so that teams can mix and match components.  For example, the [TF-GCS02 ground control station](/instruments/TF-GCS02/) can be paired with any ThunderFly autogyro through the [TFSIK01 telemetry interface](/avionics/TFSIK01/) and the open [MAVLink](https://mavlink.io/en/) protocol, enabling the switch between vehicles or even operating third-party MAVLink-compatible or [Pixhawk systems](https://pixhawk.org/) with minimal reconfiguration.

- **Airborne platforms** – Autogyros, [balloons](/instruments/TF-B1/), and specialized payload carriers cover a wide envelope of altitudes, mission endurance, and [sensor capabilities](/avionics/sensors/).  Their avionics share common hardware, software stacks, and diagnostic tools.
- **Ground segment** – [TF-GCS02](/instruments/TF-GCS02/) provides command and monitoring, while [TF-simulator](/instruments/TF-simulator/) allows for rehearsing mission control logic and payload models before deployment.
- **Support toolset** – Integration toolchain such as [TF-ATMON](/instruments/TF-ATMON/) streamlines atmospheric data acquisition, while shared avionics bridge different use-cases.

Together, ThunderFly instruments form an ecosystem where upgrades to one element (for example, a new payload or telemetry link) can be fielded across the rest of the fleet with minimal additional effort.

## Unmanned airframes range

ThunderFly maintains multiple autogyro configurations to address diverse research and operational requirements.  While each airframe emphasizes different mission profiles, they all rely on the same avionics backbone and mission-planning methodology.

| Airframe | Configuration | Primary mission focus | Typical payload capacity | Approx. price range* |
| --- | --- | --- | --- | --- |
| [**TF-G1**](https://github.com/ThunderFly-aerospace/TF-G1) | Heavy-lift autogyro platform | Carrying multi-kilogram scientific payloads and mission prototypes | Substantial research payloads with high power or mechanical integration needs | upon request (typically tens of thousands EUR) |
| [**TF-G2**](/instruments/TF-G2/) | Development kit for unmanned autogyros | Applied research, integration testing, operator training | Medium payloads (hundreds of grams) requiring frequent reconfiguration | ≈ 7 900 EUR |
| [**TF-G250**](/instruments/TF-G250/) | Aerological autogyro | Atmospheric profiling or micro-sensor payloads | Lighweight payloads with limited power and data needs | ≈ 1 000 EUR |
| [**TF-B1**](/instruments/TF-B1/) (HAB platform) | Stratospheric balloon system | High-altitude experiments | Modular atmospheric and remote-sensing payloads | 900 – 2 500 EUR |

\*Prices are indicative and depend on configuration, export conditions, accessories, and included payload interfaces.

Across the lineup, ThunderFly autogyros stand out for their inherent stability in turbulent weather at low forward speeds.  These make them ideal for atmospheric sampling, scientific payload testing. The [TF-B1 balloon platform](/instruments/TF-B1/) extends reach into the stratosphere. Because all platforms adopt standardized [ThunderFly avionics](/avionics/), teams can migrate payloads, ground control procedures, and maintenance practices from one airframe to another with minimal retraining.

### Learning resources

For those who are new to the principles of autogyro flight and would like to gain hands-on experience before working with professional research platforms, several hobby-grade RC kits are available from third parties.  
A good example is the [**LAHeli LA500 autogyro kit**](https://laheli.com/web/product.php?model=j&pid=886) or [**Durafly Auto-G2 V2**](https://hobbyking.com/en_us/durafly-pnf-auto-g2-v2-gyrocopter-w-auto-start-821mm.html). These models can also be [modified to run a PX4 autopilot](https://docs.px4.io/main/en/frames_autogyro/thunderfly_auto_g2). Both allow basic rotor handling and flight control practice using standard RC components.

> Note: These third-party kits are not affiliated with ThunderFly and are intended solely for hobby use. They are not substitutes for ThunderFly research-grade UAS.

## Telemetry and control link options

Reliable telemetry is mandatory for operations and data-processing backends.  ThunderFly systems support multiple communication tiers that can be matched to mission distance, bandwidth requirements, and regulatory constraints.

| Link technology | Typical range | Required components | Ideal use cases | Notes |
| --- | --- | --- | --- | --- |
| **Wi-Fi direct link** | Up to several hundred meters line-of-sight | Onboard Wi-Fi module and field laptop or tablet | Close-range testing, hangar integration, rapid bench diagnostics | Highest throughput but range limited; best for short sorties or pre-flight setup |
| [**TF-GCS02**](/instruments/TF-GCS02/) | Tens of kilometers with directional antennas | [TFSIK01 communication hardware](/avionics/TFSIK01/) | Primary command-and-control for [ThunderFly autogyros](#thunderfly-unmanned-autogyro-lineup) and other MAVLink-compatible UAVs | Provides telemetry, RC override, and payload data on a resilient long-range link |
| **IoT telemetry** | Coverage limited only by supported LoRaWAN/TTN networks (continent-scale) | [TFLORA01 telemetry modem](/avionics/TFLORA01/) with compatible IoT backend | Strategic tracking, low-bandwidth telemetry, and beyond-line-of-sight situational awareness | Lower data rate but unparalleled geographic reach via public or private LoRaWAN infrastructure |

Mission operators can combine these options—for example, operating a long-range MAVLink session through [TFSIK01 modem](/avionics/TFSIK01/) while using [TFLORA01](/avionics/TFLORA01/) as a redundant low-bandwidth tracker. 
