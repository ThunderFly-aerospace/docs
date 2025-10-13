---
layout: page
title: Instruments
alt_text: ThunderFly Instruments
permalink: /instruments/
has_children: true
nav_order: 10
---

## Integrated instrument ecosystem

[ThunderFly instruments](/instruments/) are designed as a cohesive toolchain that spans the entire mission lifecycle: airframe preparation, in-flight control, telemetry, data acquisition, and post-flight analysis.  Each platform leverages shared avionics, communication protocols, and payload interfaces so that teams can mix and match components without re-engineering the vehicle.  For example, the [TF-GCS02 ground control station](/instruments/TF-GCS02/) can be paired with any [ThunderFly autogyro](#thunderfly-unmanned-autogyro-lineup) through the [TFSIK01 telemetry interface](/avionics/TFSIK01/) and the open [MAVLink](https://mavlink.io/en/) protocol, enabling crews to switch between vehicles or even operate third-party MAVLink-compatible systems with minimal reconfiguration.

### Complementary roles across missions

- **Airborne platforms** – [Autogyros](#thunderfly-unmanned-autogyro-lineup), [balloons](/instruments/TF-B1/), and specialized payload carriers cover a wide envelope of altitudes, mission endurance, and sensor capabilities.  Their avionics share common wiring, software stacks, and diagnostic tools.
- **Ground segment** – [TF-GCS02](/instruments/TF-GCS02/) provides expedition-ready command and monitoring, while [TF-simulator](/instruments/TF-simulator/) allows teams to rehearse missions with identical control logic and payload models before deployment.
- **Support tooling** – Integration helpers such as [TF-ATMON](/instruments/TF-ATMON/) streamline atmospheric data workflows, while shared accessories like [TFSIK01](/avionics/TFSIK01/) and [TFLORA01](/avionics/TFLORA01/) bridge different telemetry backhauls.

Together, these [instruments](/instruments/) form an ecosystem where upgrades to one element (for example, a new payload or telemetry link) can be fielded across the rest of the fleet with minimal additional effort.

## ThunderFly unmanned autogyro lineup

ThunderFly maintains multiple autogyro configurations to address diverse research and operational requirements.  While each airframe emphasizes different mission profiles, they all rely on the same avionics backbone and mission-planning methodology.  The following overview highlights the most relevant characteristics to help teams choose the best starting point without delving into every detailed specification page.

| Airframe | Configuration | Primary mission focus | Distinguishing features | Typical payload capacity |
| --- | --- | --- | --- | --- |
| [**TF-G1**](https://github.com/ThunderFly-aerospace/TF-G1) | Heavy-lift autogyro platform | Carrying multi-kilogram scientific payloads and mission prototypes | Proven workhorse for testing complex instruments and robust avionics in field conditions | Substantial research payloads with high power or mechanical integration needs |
| [**TF-G2**](/instruments/TF-G2/) | Development kit for unmanned autogyros | Applied research, integration testing, operator training | Modular structure with quick-swap payload bays and comprehensive documentation for customization | Medium payloads requiring frequent reconfiguration |
| [**TF-G250**](/instruments/TF-G250/) | Operational aerological autogyro | Long-endurance atmospheric profiling and sensor payloads | Optimized rotor system and environmental sealing for harsh-weather sampling; proven in demanding meteorological campaigns | Larger scientific payloads with extended power and data needs |
| [**TF-simulator**](/instruments/TF-simulator/) (virtual airframes) | High-fidelity mission simulator | Training, rehearsal, validation of control strategies | Replicates flight dynamics of physical airframes (including autogyros and balloons) for risk-free testing and crew coordination | Supports virtual payload integration and mission scripting |
| [**TF-B1**](/instruments/TF-B1/) (balloon platform) | Stratospheric balloon system | High-altitude experiments and persistent loitering | Interfaces with shared avionics stack and payload handling to extend missions beyond rotorcraft envelope | Modular atmospheric and remote-sensing payloads |

Across the lineup, [ThunderFly autogyros](#thunderfly-unmanned-autogyro-lineup) stand out for their inherent stability in turbulent weather, precise station-keeping at low forward speeds, and ability to safely winch or deploy probes without complex rotorcraft control laws.  These traits make them ideal for atmospheric sampling, payload testing, and missions that demand accurate hovering over a point of interest.  The [TF-B1 balloon platform](/instruments/TF-B1/) extends reach into the stratosphere for long-duration sensing, while the [TF-simulator](/instruments/TF-simulator/) enables mission rehearsal so operators can transfer skills directly to field deployments.  Because all platforms adopt standardized [ThunderFly avionics](/avionics/) and communication interfaces such as [TFSIK01](/avionics/TFSIK01/) and [TFLORA01](/avionics/TFLORA01/), teams can migrate payloads, ground control procedures, and maintenance practices from one airframe to another with minimal retraining.

## Telemetry and control link options

Reliable telemetry is a cornerstone of collaborative operations between airborne instruments, ground crews, and data-processing backends.  ThunderFly systems support multiple communication tiers that can be matched to mission distance, bandwidth requirements, and regulatory constraints.

| Link technology | Typical range | Required components | Ideal use cases | Notes |
| --- | --- | --- | --- | --- |
| **Wi-Fi direct link** | Up to several hundred meters line-of-sight | Onboard Wi-Fi module and field laptop or tablet | Close-range testing, hangar integration, rapid bench diagnostics | Highest throughput but range limited; best for short sorties or pre-flight setup |
| [**TF-GCS02**](/instruments/TF-GCS02/) + [**TFSIK01**](/avionics/TFSIK01/) (MAVLink) | Tens of kilometers with directional antennas | [TF-GCS02 ground control station](/instruments/TF-GCS02/) paired with [TFSIK01 communication interface](/avionics/TFSIK01/) | Primary command-and-control for [ThunderFly autogyros](#thunderfly-unmanned-autogyro-lineup) and other MAVLink-compatible UAVs | Provides telemetry, RC override, and payload data on a resilient long-range link |
| [**TFLORA01**](/avionics/TFLORA01/) IoT telemetry | Coverage limited only by supported LoRaWAN/TTN networks (continent-scale) | [TFLORA01 telemetry modem](/avionics/TFLORA01/) with compatible IoT backend | Strategic tracking, low-bandwidth telemetry, and beyond-line-of-sight situational awareness | Lower data rate but unparalleled geographic reach via public or private LoRaWAN infrastructure |

Mission planners can combine these options—for example, operating a long-range MAVLink session through [TF-GCS02](/instruments/TF-GCS02/) while using [TFLORA01](/avionics/TFLORA01/) as a redundant low-bandwidth tracker.  Shared protocols and hardware interfaces ensure that telemetry upgrades cascade throughout the instrument family without bespoke integration effort.

