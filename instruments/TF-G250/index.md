---
title: "TF-G250 - Unmanned Aerological Autogyro"
layout: page
permalink: /instruments/TF-G250
parent: Instruments
nav_order: "3"
---

# TF-G250 - Unmanned Aerological Autogyro

The TF-G250 is a miniature unmanned autogyro specifically developed for atmospheric boundary layer measurements. It serves as a practical and ecological alternative to conventional balloon-based radiosondes, performing vertical profiling of key meteorological parameters: temperature, humidity, wind speed and direction, and atmospheric pressure.

The TF-G250 autogyro is designed for easy handling, deployment, and maintenance, ensuring affordability and robustness in diverse meteorological conditions. Its compact and lightweight structure (below 250 grams, complying with the [European C0 category](https://www.easa.europa.eu/en/domains/drones-air-mobility/operating-drone/open-category-low-risk-civil-drones)) simplifies transport and storage, making it ideal for rapid deployment scenarios.

![TF-G250 during flight](TF-G250_flight.png)

The TF-G250 addresses a rapidly growing global demand for cost-effective, reusable atmospheric measurement tools. Unlike traditional solutions, the TF-G250  meteo autogyro drone offers significant operational advantages due to its lightweight, absence of parachute, inherent safety mechanisms, and safe-descent capability.

## Key Design Features

* Integrated sensor payload for basic atmospheric measurements (temperature, humidity, pressure, wind speed, and direction)
* Does not require energy for the descent phase, enabling reduced battery weight
* Automatic fail-safe landing without requiring parachutes or additional mechanisms
* Effective operational altitude up to 3240 meters above ground
* Real-time telemetry for atmospheric data publication and processing
* Extremely low maintenance with easy repairability
* Optimized rotor design allows manual spin-up by hand before launch, enabling takeoff even without ambient wind
* Low acoustic signature

These design choices provide the TF-G250 with a distinct competitive edge, allowing safe and controlled descent while significantly improving energy efficiency.

## Technical Specifications

The following table provides a detailed overview of the key meteorological performance parameters of the TF-G250. These specifications are based on the integrated  sensors.

| Parameter                     | Specification                                           |
| ----------------------------- | ------------------------------------------------------- |
| Maximum Take-off Weight       | < 250 g (C0 category)                                   |
| Operational Altitude          | ~3.2 km AGL self-powered, ~32km AMSL balloon-launched   |
| Temperature Range             | –40 to +40 °C                                           |
| Temperature Accuracy          | ±0.2 °C (typical)                                       |
| Temperature Resolution        | 0.01 °C                                                 |
| Relative Humidity Range       | 0–100 %RH                                               |
| Relative Humidity Accuracy    | ±1.5 % RH (typical)                                     |
| Relative Humidity Resolution  | 0.01 % RH                                               |
| Pressure Range                | 3–110 kPa                                               |
| Pressure Accuracy             | ±20 Pa (typical)                                        |
| Pressure Resolution           | 1 Pa                                                    |
| Wind Speed Range              | TBD                                                     |
| Wind Speed Accuracy           | ±0.2 m/s                                                |
| Wind Speed Resolution         | 0.1 m/s                                                 |
| Wind Direction Range          | 0 to 360°                                               |
| Wind Direction Accuracy       | ±2°                                                     |
| Wind Direction Resolution     | ±0.1°                                                   |
| Effective Vertical Resolution | 5 m                                                     |
| Data Output Format            | BUFR-compatible                                         |
| Telemetry                     | Real-time via onboard radio modem                       |

## Meteorological Applications

The TF-G250 is primarily designed for vertical atmospheric profiling, making it particularly suited for capturing high-resolution meteorological data throughout the atmospheric boundary layer.

* **Temperature and Humidity Measurements:** Temperature and relative humidity are measured directly by a fast-response atmospheric sensor probe, positioned in the undisturbed airflow to ensure high accuracy across vertical profiles essential for weather forecasting, including storm intensity and its extent.
* **Wind Speed and Direction:** Wind speed and direction are measured directly during flight using the aircraft's controlled circular trajectory, which enables the autopilot to provide real-time estimates of both parameters with high accuracy.
* **Atmospheric Pressure:** Air pressure is measured directly by multiple onboard barometric sensors. These measurements are fused in real time together with absolute position data obtained from the GNSS navigation receiver to ensure high accuracy.

### Monitoring of Thermic and Convective Currents

Thanks to its controlled flight capabilities, the TF-G250 enables not only vertical profiling but also real-time localization and measurement of convective airflows. This makes it a valuable tool for identifying and analyzing vertical air movements that are essential for aviation forecasting and atmospheric research.


### Boundary Layer Sounding

The TF-G250 is ideally suited for detailed [atmospheric boundary layer (ABL)](https://en.wikipedia.org/wiki/Planetary_boundary_layer) soundings. The example below illustrates a typical measurement campaign with local atmospheric differences captured in three visualizations:

![Measurement Flight Path](Measurement_flight.png)

3D trajectory showing the flight path used for boundary layer sampling.

![Temperature and Humidity Profile](Temperature_and_relative_humidity_profile.png)

Temperature and relative humidity are plotted against altitude above ground level (AGL). A slight difference is visible between the ascent and descent, with increased humidity observed during the descent due to the overflight of vegetated terrain near a water body.

![Wind Hodograph](wind_hodograph.png)

Hodograph of wind speed and direction, color-coded by altitude AGL. Wind structure indicates turbulence within the sampled boundary layer.*

In this particular mission, the takeoff and landing occurred at different locations. During landing, the sensor passed over a grassy area near a water surface, which resulted in a localized increase in measured relative humidity. These variations highlight the sensitivity of the TF-G250 system to microclimatic effects within the ABL.


## Operational Flight Procedure

The TF-G250 supports two main operational procedures for atmospheric profiling:

1. **Automatic Powered Flight:** The autogyro performs vertical profiling by executing a controlled spiral ascent followed by a descent. This method allows adaptation to wind conditions, including straight vertical climbs into the wind when spiral flight is less effective.

<div style="width:100%; padding-top: 56.25%;position: relative;overflow: hidden;">
  <iframe style="width: 100%;height: 100%;position: absolute;top: 0;left: 0;" src="https://www.youtube.com/embed/DTOk--t4eaM?loop=1&playlist=DTOk--t4eaM" frameborder="0" allowfullscreen>
  </iframe>
</div>


2. **Balloon-Assisted Deployment:** Radiosonde-like flight - for higher altitudes beyond the reach of the autogyro's own propulsion, the TF-G250 can be carried aloft by a traditional meteorological balloon. Upon reaching the desired altitude, the TF-G250 detaches and performs a controlled descent, collecting atmospheric data during both the ascent (via telemetry relay) and the descent phase.

Future enhancements may include ground-based automation for launch, recovery, and servicing of both operational modes.

### Data Processing

Meteorological data collected by the TF-G250 are processed using standard meteorological software such as [thundeR](https://bczernecki.github.io/thundeR/) and [SHARPpy](https://github.com/sharppy/SHARPpy), with outputs available in the [BUFR format](https://en.wikipedia.org/wiki/BUFR) for ease of integration into existing meteorological workflows.

