---
title: "TF-G2 - Unmanned Autogyro Development Kit"
layout: page
permalink: /instruments/TF-G2
parent: Instruments
nav_order: "2"
---

# TF-G2 - Unmanned Autogyro Development Kit

Check the introductory video to quickly get an overview: 
[![ThuderFly_TFG2_training_autogyro_prototype](https://user-images.githubusercontent.com/5196729/144823035-37a70a1a-de21-4eb6-ab80-2aa2d4ea78db.gif)](http://www.youtube.com/watch?v=6PtS-MwnM_8)

[TF-G2](https://www.thunderfly.cz/tf-g2.html) Autogyro is well-suited for training and for gaining experience with autogyro mission planning. TF-G2 is limited to light payloads, but it shares all the specific properties of larger autogyros in our offering. It may find application in less demanding flight operations; however, its main purpose is to be a tool for low-cost application practice. The autogyro’s small size leads to easy transport, repairs, and maintenance.
To enhance the ease of learning autogyro technology, we made it possible to [simulate TF-G2 flight](/instruments/TF-simulator) before the real flight.

![TF-G2 during flight](https://raw.githubusercontent.com/ThunderFly-aerospace/TF-G2/4s/doc/img/TF-G2_fly_clouds.jpg)

## The main design highlights

  * Micro payload load capacity suitable for multiple types of [TF-ATMON atmospheric sensors](/instruments/TF-ATMON)
  * Low audible noise
  * High maneuverability and agility
  * Extreme tolerance to rotor blade damage
  * Passive autorotation-based recovery
  * Repairable and low maintenance
  * Use of 3D printing flexibility
  * [Simulation model available](/instruments/TF-simulator/Vehicles#tf-g2-uav-autogyro)
  * [Car roof takeoff capable](https://youtu.be/3rhRHRPYnNQ)

## Technical specifications

| Parameter | Value / Description |
|------------|--------------------|
| Maximum takeoff weight | 1.5 kg |
| Payload capacity | up to 100 g |
| Rotor diameter | 0.8 – 1.05 m |
| Airspeed flight range | 7 – 25 m/s |
| Crosswind takeoff and landing capability | up to 15 m/s |
| Wind gust resistance | up to 10 m/s s⁻¹ (instantaneous wind acceleration)  |
| Construction | Easily repairable, open-source design and documentation |
| Flight modes | Manual, stabilized, and automatic flight support |
| Launch methods | Hand or car-roof takeoff |
| EASA Category | C2 |

Optionally measured quantities: Temperature, humidity, airborne particles (PM₀․₅–PM₁₀), ionizing radiation, gases (CO₂, O₃, SOₓ, NOₓ …), thermal imaging matrix, and electric field intensity. Additional sensor types can be integrated on request

## Application Examples

Here are some examples of use cases for TF-G2 as a lightweight sensor carrier. These application-specific use cases of the integrated sensing possibilities are provided by additional avionics. The default onboard sensors measure position, time, wind speed, direction, velocity, and atmospheric pressure.

### Particulate matter sensing

Particulate matter sensing in the atmosphere is a scientific technique used to monitor and measure the concentration of small solid particles suspended in air, often termed aerosols. These particles, typically categorized by their size, such as PM2.5 and PM10, can originate from various sources, including combustion processes, industrial emissions, vehicle exhausts, and natural phenomena like volcanic activity or dust storms. Sensing and monitoring particulate matter is crucial for environmental health, as high levels can severely impact air quality, contributing to respiratory and cardiovascular diseases. Moreover, this data aids meteorological predictions and climate models, as particulates influence atmospheric visibility and can affect the Earth's radiation balance. The TF-G2 autogyro could be equipped with [TFPM02](/avionics/TFPM02/) particulate matter sensor to measure the concentration of particulate matter in the specified air volume. 

<div style="width:100%; padding-top: 56.25%; position: relative; overflow: hidden;">
  <iframe 
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" 
    src="https://www.youtube.com/embed/KUhktPDEi8I?loop=1&playlist=KUhktPDEi8I" 
    frameborder="0" 
    allowfullscreen>
  </iframe>
</div>


### Humidity and temperature sensing

Humidity and temperature sensing in [atmospheric vertical sounding](https://en.wikipedia.org/wiki/Atmospheric_sounding) involves the measurement of atmospheric moisture content and temperature at various altitudes. Instruments like the [TFHT01 sensor](/avionics/TFHT01) could be used. These compact and lightweight sensors are designed specifically for UAV applications.

![TF-G2 atmospheric sounding experiment](https://raw.githubusercontent.com/ThunderFly-aerospace/TFHT01/TFHT01B/doc/img/TFHT_vertical_profile_measurement.png)

An example of an atmospheric profiling experiment. The time difference between the reference and the experiment was around 6 hours. 

### Electric field monitoring

The charged particles present in thunderstorms create strong electric fields, which can be detected and monitored by [THUNDERMILL01 sensor](/avionics/THUNDERMILL01). The TF-G2 autogyro, equipped with this sensor, can navigate challenging weather conditions and provide real-time data on the strength and spatial distribution of the electric fields. This UAV-autogyro technology offers a unique, mobile platform to safely investigate these intense electrical phenomena.

![TF-G2 with installed THUNDERMILL electric field sensor](https://raw.githubusercontent.com/ThunderFly-aerospace/TF-G2/4s/doc/img/TF-G2_THUNDERMILL.jpg)

### Ionizing radiation monitoring

Ionizing radiation monitoring in the atmosphere involves detecting and quantifying radioactive particles using specialized devices like semiconductor-based ionizing radiation [AIRDOS03](/avionics/AIRDOS03) spectrometer and dosimeter. This instrument measures the intensity and spectral distribution of ionizing radiation, such as alpha, beta, gamma, and X-ray emissions that can originate from natural sources or human activities. The compact semiconductor-based devices allow for the detection and quantification of radiation intensity. Monitoring atmospheric ionizing radiation for assessing environmental radiation hazards, managing nuclear emergencies, and supporting research in fields such as meteorology, geology, and climate science.

