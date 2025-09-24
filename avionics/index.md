---
layout: page
title: Avionics
alt_text: Avionics
permalink: /avionics/
has_children: true
has_toc: true
nav_order: 20
---


## Avionics Components  

ThunderFly's avionics system consists of **high-performance hardware** designed to enhance the capabilities of standard unmanned aerial vehicles (multicopter, airplane, etc.). ThunderFly avionics components are built for seamless integration into existing UAV platforms like [PX4](https://px4.io/) or [Ardupilot](https://ardupilot.org/).  The following clickable diagram shows an example interconnection of different ThunderFly avionics components; usually, only a fraction of this diagram is used in the actual UAV:

```mermaid
flowchart TD


%% Nodes
FC["TFPILOTBASEBOARD01<br/>(Pixhawk-compatible flight controller)"]
TFLORA01[TFLORA01]
TFI2CADT01[TFI2CADT01]
TFESC02[TFESC02]
TFESC03[TFESC03]
TFSBEC01[TFSBEC01]
TFI2CEXT01[TFI2CEXT01]
TFPITOT01[TFPITOT01]
TFHT01[TFHT01]
TFHT02[TFHT02]
TFCO201[TFCO201]
TFRPM01[TFRPM01]
TFSLOT01[TFSLOT01]
TFGPS01[TFGPS01]
TFGPSLITE02[TFGPSLITE02]
TFUSBSERIAL01[TFUSBSERIAL01]
TFUNIPAYLOAD01[TFUNIPAYLOAD01]
TFSIK01[TFSIK01]
TFPROBE01[TFPROBE01]
BATT[Battery Pack]


%% Point-to-point cable instances (unique IDs, same visible label)
CAB15_HT01["TFCAB15I2C01"]
CAB20_HT02["TFCAB30I2C01"]
CAB20_RPM["TFCAB30I2C01"]
CAB20_SLOT["TFCAB30I2C01"]
CAB45_PITOT["TFCAB45I2C01"]


%% Edges (plain)
FC <--> TFLORA
FC <--> TFI2CADT01
FC <--> TFESC02
FC <--> TFESC03
FC <--> TFUSBSERIAL01
FC <--> TFSIK01
FC <--> TFUNIPAYLOAD01

TFI2CADT01 <--> TFI2CEXT01
TFI2CADT01 <--> TFCO201


%% Sensors over dedicated cables
TFI2CADT01 <--> CAB15_HT01 <--> TFHT01
TFI2CADT01 <--> CAB20_HT02 <--> TFHT02
TFI2CADT01 <--> CAB20_RPM <--> TFRPM01
TFI2CADT01 <--> CAB20_SLOT <--> TFSLOT01
TFI2CEXT01 <--> CAB45_PITOT <--> TFPITOT01


%% Probe on TFRPM01
TFPROBE01 -->  TFRPM01


%% Other peripherals
TFGPS01 --> FC
TFGPSLITE02 --> FC

%% Power
BATT --> FC
BATT --> TFESC02
BATT --> TFESC03
BATT --> TFSBEC01

TFSBEC01 --> FC

%% Clickable docs
click TFLORA01 "https://docs.thunderfly.cz/avionics/TFLORA01/" "TFLORA01 Documentation"
click TFI2CADT01 "https://docs.thunderfly.cz/avionics/TFI2CADT01/" "TFI2CADT01 Documentation"
click TFI2CEXT01 "https://docs.thunderfly.cz/avionics/TFI2CEXT01/" "TFI2CEXT01 Documentation"
click TFPITOT01 "https://docs.thunderfly.cz/avionics/TFPITOT01/" "TFPITOT01 Documentation"
click TFHT01 "https://docs.thunderfly.cz/avionics/TFHT01/" "TFHT01 Documentation"
click TFHT02 "https://docs.thunderfly.cz/avionics/TFHT02/" "TFHT02 Documentation"
click TFCO201 "https://docs.thunderfly.cz/avionics/TFCO201/" "TFHT02 Documentation"
click TFRPM01 "https://docs.thunderfly.cz/avionics/TFRPM01/" "TFRPM01 Documentation"
click TFPROBE01 "https://docs.thunderfly.cz/avionics/TFRPM01/probe#tfprobe01a---omnipolar-magnetic-and-reflective-optical-sensor-probe" "TFPROBE01 Documentation"
click TFSLOT01 "https://docs.thunderfly.cz/avionics/TFSLOT01/" "TFSLOT01 Documentation"
click TFGPS01 "https://docs.thunderfly.cz/avionics/TFGPS01/" "TFGPS01 Documentation"
click TFGPSLITE02 "https://docs.thunderfly.cz/avionics/TFGPSLITE02/" "TFGPSLITE02 Documentation"
click TFUSBSERIAL01 "https://docs.thunderfly.cz/avionics/TFUSBSERIAL01/" "TFUSBSERIAL01 Documentation"
click TFUNIPAYLOAD01 "https://docs.thunderfly.cz/avionics/TFUNIPAYLOAD01/" "TFUNIPAYLOAD01 Documentation"
click TFSIK01 "https://docs.thunderfly.cz/avionics/TFSIK01/" "TFSIK01 Documentation"
click TFESC02 "https://docs.thunderfly.cz/avionics/TFESC02/" "TFESC02 Documentation"
click TFESC03 "https://docs.thunderfly.cz/avionics/TFESC03/" "TFESC03 Documentation"
click CAB15_HT01 "https://docs.thunderfly.cz/avionics/TFCAB01/" "Cables Documentation"
click CAB20_HT02 "https://docs.thunderfly.cz/avionics/TFCAB01/" "Cables Documentation"
click CAB20_RPM "https://docs.thunderfly.cz/avionics/TFCAB01/" "Cables Documentation"
click CAB20_SLOT "https://docs.thunderfly.cz/avionics/TFCAB01/" "Cables Documentation"
click CAB45_PITOT "https://docs.thunderfly.cz/avionics/TFCAB01/" "Cables Documentation"
```

The development was originally motivated by the hardware requirements of [TF-ATMON](https://docs.thunderfly.cz/instruments/TF-ATMON), which focuses on atmospheric measurements in harsh conditions. Therefore, the solution covers the entire workflow — from sensors and in-flight data acquisition, through data transmission, to final visualization — and this use case shaped the design of avionics. All modules are developed and manufactured in Europe to meet common aerospace and research standards.  

### ThunderFly Form Factor

ThunderFly avionics modules are designed according to an internal PCB form factor standard. This allows for reducing weight and maintaining compatibility between different devices.

![TF PCB form factor](TFPCB_avionics.png)

The dimensions of the PCB are defined by three parameters:

- **a** – additional width (integer, may also be 0)  
- **b** – additional length (integer)  
- **c** – additional mounting holes positions (integer, may also be 0)  

> Most commonly, the module width is 15 mm or 20 mm (e.g., a=0 or a=5), depending on the JST-GH connector number of pins (typically 4-pin for I²C).
> Mounting notches with a radius of 1.5 mm are positioned on both sides of the PCB. May be skipped (even asymmetrically) for relevant construction reasons. Their placement is measured from the connector edge.

#### Status Indicators

Each ThunderFly avionics module is equipped with status LEDs to provide quick visual feedback during operation. Typical meaning is as follows: 

- **Green LED** – usually indicates either power presence or that the module is functioning correctly.  
- **Red LED** – typically used for error or fault indication, highlighting abnormal states.  
- **Other colors** (blue, orange, yellow) – reserved for different operational statuses depending on the specific module.  

#### Example of Enclosure Mounting

The standardized PCB form factor allows straightforward design of **protective enclosures**.   Modules can be fixed inside 3D-printed or CNC-machined cases using the PCB notches. PCB then slides into the slots of the enclosure, and notches enable secure mounting with just two screws.

![Module in enclosure, perspective view](TFPCB_box.png)

![ThunderFly module in enclosure, top view, with screws](TFPCB_box_mounting_screws.png)

This approach results in avionics modules that are mechanically protected while still being lightweight and accessible to service.  The described modular block concept allows either grouping multiple avionics units together or distributing them in different airframe compartments, depending on application requirements.

### How to Order

You can order avionics components in the following ways:

- **Directly from ThunderFly** — use our [Contact us](https://www.thunderfly.cz/contact-us.html) page to request a quotation, check lead times, or discuss bulk pricing.
- **Online marketplaces**
  - **[Tindie](https://www.tindie.com/stores/thunderfly/)** — suitable for worldwide orders
  - **[Lectronz](https://lectronz.com/stores/thunderfly)** — recommended for customers in Europe.

### Components Pricing

The following table lists wholesale prices for avionics components for orders up to 50 units. For bulk pricing, unlisted items or special requirements, please directly contact sale@thunderfly.cz.

| Product Name       | Price (1–3 pcs) | Price (4–10 pcs) | Price (11–50 pcs) |
|--------------------|------------------|-------------------|--------------------|
| [TFRPM01](https://docs.thunderfly.cz/avionics/TFRPM01/) | €74,00 | €70,30 | €66,60 |
| [TFPROBE01](https://docs.thunderfly.cz/avionics/TFRPM01/probe#tfprobe01a---omnipolar-magnetic-and-reflective-optical-sensor-probe) | €27,00 | €25,65 | €24,30 |
| [TFI2CADT01](https://docs.thunderfly.cz/avionics/TFI2CADT01/) | €89,00 | €84,55 | €80,10 |
| [TFSLOT01](https://docs.thunderfly.cz/avionics/TFSLOT01/) | €298,00 | €283,10 | €268,20 |
| [TFHT01](https://docs.thunderfly.cz/avionics/TFHT01/) | €81,00 | €76,95 | €72,90 |
| [TFHT02](https://docs.thunderfly.cz/avionics/TFHT02/) |	€60,75 | €57,71	| €54,68 |
| [TFUSBSERIAL01](https://docs.thunderfly.cz/avionics/TFUSBSERIAL01/) | €86,00 | €81,70 | €77,40 |
| [TFPITOT01](https://docs.thunderfly.cz/avionics/TFPITOT01/) | €148,00 | €140,60 | €133,20 |
| [TFGPS01](https://docs.thunderfly.cz/avionics/TFGPS01/) | €280,00 | €266,00 | €252,00 |
| [TFGPSLITE02](https://docs.thunderfly.cz/avionics/TFGPSLITE02/) | €143,00 | €135,85 | €128,70 |
| [TFI2CEXT01](https://docs.thunderfly.cz/avionics/TFI2CEXT01/) | €92,00 | €87,40 | €82,80 |
| [TFSIK01](https://docs.thunderfly.cz/avionics/TFSIK01/) | €323,83 | €307,64 | €291,45 |
| [TFCAB15I2C01](https://docs.thunderfly.cz/avionics/TFCAB01/) | €8,00 | €7,60 | €7,20 |
| [TFCAB30I2C01](https://docs.thunderfly.cz/avionics/TFCAB01/) | €8,50 | €8,08 | €7,65 |
| [TFCAB45I2C01](https://docs.thunderfly.cz/avionics/TFCAB01/) | €9,00 | €8,55 | €8,10 |

> **Note:**
> - All prices are in EUR and **exclude VAT and shipping costs**.
> - Pricing valid from **28 August 2025**.
> - **Payment**: In advance via bank transfer based on a proforma invoice.
> - **Shipping**: Costs depend on destination and carrier; quotes available on request.
> - **Lead time**: Standard quantities are usually shipped within a week, with a maximum lead time of up to 4 weeks. Lead times for bulk orders may vary.
> - **Warranty**: Standard 6-month warranty. Extended warranty options are available on request.

