---
layout: page
title: "TFPM02 - UAS Particulate matter sensor"
permalink: /avionics/TFPM02/
parent: Sensors
nav_order: "54"
---

# TFPM02 - Particulate Matter Sensor for ThunderFly TF-ATMON system

The TFPM02 sensor is a modular device for measuring particulate matter concentration in atmospheric research applications, particularly within the [TF-ATMON system](/instruments/TF-ATMON). It exists in two hardware variants:

* **TFPM02A** based on the Sensirion **SPS30** sensor
* **TFPM02B** based on the Sensirion **SEN5x** sensor

Each variant offers distinct advantages and is optimized for different types of measurements.

---

## TFPM02A – SPS30-based variant

This variant is built around the [Sensirion SPS30](https://sensirion.com/products/catalog/SPS30/) laser particulate matter sensor. It provides both mass and number concentrations of aerosol particles.

### Key Features

* **Mass concentration** for PM1.0, PM2.5, PM4, PM10: 0 – 1000 μg/m³ (Accuracy ±10%)
* **Number concentration** for PM0.5, PM1.0, PM2.5, PM4, PM10: 0 – 3000 #/cm³
* Compact and lightweight design suitable for UAV deployment

> **Note:** This variant does **not** provide ambient temperature or humidity data. For environmental compensation, it is recommended to use it with the [TFHT02 sensor](/avionics/TFHT02).

### Connectivity

The modified SPS30 sensor is connected to PX4 autopilot-supported hardware using a **ZHR-5 to JST-GH** cable. Sensor is then controlled directly by the autopilot firmware and data transmitted via MAVLink.

![Bottom view on TFPM02A](https://raw.githubusercontent.com/ThunderFly-aerospace/TFPM02/refs/heads/TFPM02A/doc/img/TFPM02_bottom.jpg)

![Top view on TFPM02A](https://raw.githubusercontent.com/ThunderFly-aerospace/TFPM02/refs/heads/TFPM02A/doc/img/TFPM02_top.jpg)

---

## TFPM02B – SEN55-based variant

The TFPM02B variant integrates the [Sensirion SEN55](https://sensirion.com/products/catalog/SEN55/) sensor module. This sensor extends capabilities by including environmental measurements beyond just aerosols.

### Key Features

* **Mass concentration** for PM1.0, PM2.5, PM4, PM10: 0 – 1000 μg/m³ (Accuracy ±10%)
* **Temperature**: -10 to 50 °C (Accuracy 0.45 °C)
* **Humidity**: 0 – 90 %RH (Accuracy ±4.5 %RH)
* **VOC**: 1 – 500 (corresponding to 0 – 1000 ppm ethanol equivalent)
* **NOx**: 1 – 500 (corresponding to 100 to 300 ppb of NO2)


> **Note:** The SEN55 sensor **does not** provide number concentration data. If this metric is important for your application, use TFPM02A instead.

### Connectivity

The sensor is connected directly to the PX4 autopilot via **JST-GH** cable over I²C. Output is translated to MAVLink via uOrb messages, enabling logging and real-time transmission to [TF-ATMON enabled GCS](/instruments/TF-GCS02).

![View on TFPM02B sensor](https://raw.githubusercontent.com/ThunderFly-aerospace/TFPM02/refs/heads/TFPM02B/doc/img/SEN5x.jpg)

---

## Availability

The ThunderFly TFPM02 sensors (both A and B variants) are commercially available from [ThunderFly s.r.o.](https://www.thunderfly.cz/). Please contact [info@thunderfly.cz](mailto:info@thunderfly.cz) for inquiries, pricing, or customization.

---

## Demonstration

A typical use-case and demonstration of TFPM02 sensor in flight onboard a [TF-G2 autogyro](https://github.com/ThunderFly-aerospace/TF-G2) can be viewed in the following video:

[![TF-ATMON particulate matter sensing demonstration](https://img.youtube.com/vi/KUhktPDEi8I/hqdefault.jpg)](https://www.youtube.com/watch?v=KUhktPDEi8I)

