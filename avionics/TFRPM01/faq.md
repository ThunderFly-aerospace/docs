---
layout: page
title: "Frequently asked questions"
permalink: /avionics/TFRPM01/faq
parent: "TFRPM01: RPM sensor"
grand_parent: Avionics
nav_order: "2"
---


# FAQ
## What about the measurement resolution of the RPM?

RPM measurement [resolution](https://en.wikipedia.org/wiki/Sensor#Resolution) depends on [pooling interval](https://docs.px4.io/main/en/advanced_config/parameter_reference.html#PCF8583_POOL) and the number of pulses per revolution.

RPM is calculated from measured values (pulses per interval) as follows

![RPM equation](https://latex.codecogs.com/png.image?\dpi{110}RPM=\frac{N_c60}{N\tau})

Therefore the resolution of measured RPM is the follows:

![Resolution equation](https://latex.codecogs.com/png.image?\dpi{110}Res=\frac{60}{N\tau})


Where:
  * N is pulses per revolution
  * τ is the pooling interval in seconds
  * Nc is pules counted during the measurement pooling interval
  * Res is the absolute resolution of measurement in +/- RPM

Therefore the absolute resolution of the sensor is independent of the current RPM measured and remains constant depending on sensor configuration, however, relative resolution increases with the RPM measured.  The absolute resolution strongly depends on the length of the pooling interval (a longer interval gets better resolution). The resolution also increases with the number of pulses per revolution, where more pulses per revolution give better RPM resolution. Related terms like precision and accuracy are more difficult to analyze because they depend on hardware and firmware versions of Pixhawk, but these errors could be neglected in the usual use cases.

## Does it connect to RPM output from ESC?

Generally yes, the TFRPM could be connected to revolution output from an ESC in case the output logic confirms to 5V TTL.
The limitation is the RPM resolution here because many ESCs get one pulse per revolution. Please take a look at the formula above for an explanation.

## Could be used for internal combustion engines?

Yes, it could measure the RPM of the IC Engine. However, it needs a pulse signal to count the rotation speed. The pulsed signal could be either obtained either from [Electronic control unit](https://en.wikipedia.org/wiki/Electronic_control_unit) (ECU) or from an [Optical or magnetic probe](https://github.com/ThunderFly-aerospace/TFPROBE01) mounted on the proper location of the engine unit. Direct connection of TFRPM to ignition or sensing coils is not possible without signal conditioning, because the voltage of signals coming from coils will likely destroy the TTL-based RPM input of TFRPM. Required signal conditioning could be realized by a resistor network in many cases. Contact [ThunderFly s.r.o.](https://www.thunderfly.cz/contact-us.html) in case you need professional support.

